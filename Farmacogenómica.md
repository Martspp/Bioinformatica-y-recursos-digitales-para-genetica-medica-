# Introducción
ACMG clasifica la relación variante–enfermedad; PGx interpreta la relación variante/haplotipo–función–fármaco.

| Problema bioinformático | Recurso principal | Qué debe resolverse |
|---|---|---|
| Selección de variantes del ensayo | AMP PGx Working Group | Alelos Tier 1 y Tier 2 |
| Nomenclatura de haplotipos | PharmVar | Definición oficial de *star alleles* |
| Asignación automatizada | PharmCAT | VCF → diplotipo → fenotipo |
| Función del alelo | CPIC/ClinPGx y PharmVar | Normal, disminuida, nula, aumentada o incierta |
| Traducción a fenotipo | CPIC | PM, IM, NM, RM o UM |
| Recomendación terapéutica | CPIC y DPWG | Dosis, alternativa o monitorización |
| CNV e híbridos de CYP2D6 | AMP + PharmVar + validación específica | Copias, estructura y alelo duplicado |
| HLA farmacogenómico | Guías gen–fármaco y métodos HLA validados | Tipificación alélica de alta resolución |
| Validación del pipeline | AMP/CAP y validación local | Sensibilidad, especificidad, precisión y reproducibilidad |

detección de variantes → asignación de haplotipos/star alleles → diplotipo → fenotipo metabolizador → recomendación farmacológica.

La diferencia clave respecto a enfermedad rara es que una variante farmacogenómica normalmente no se clasifica como patogénica/VUS/benigna. Se determina si define un alelo, qué función tiene ese alelo y cómo modifica la respuesta a un medicamento.

# Guías y recursos por etapa
| Etapa del análisis           | Pregunta                                                            | Guía o recurso principal                         | Para qué sirve                                                                          |
| ---------------------------- | ------------------------------------------------------------------- | ------------------------------------------------ | --------------------------------------------------------------------------------------- |
| Diseño del ensayo            | ¿Qué variantes debe detectar el laboratorio?                        | **AMP Pharmacogenomics Working Group**           | Define alelos mínimos **Tier 1** y alelos adicionales **Tier 2** para genes específicos |
| Nomenclatura                 | ¿Qué variantes forman cada alelo estrella?                          | **PharmVar**                                     | Nomenclatura oficial de haplotipos y subalelos                                          |
| Llamado de haplotipos        | ¿Qué combinación de alelos tiene el paciente?                       | PharmVar + especificaciones del software         | Traduce variantes, fase y CNV a *star alleles*                                          |
| Diplotipo → función          | ¿Cuál es la actividad funcional del diplotipo?                      | **CPIC/ClinPGx** y tablas de función de PharmVar | Asigna función normal, disminuida, nula, aumentada o incierta                           |
| Función → fenotipo           | ¿Es metabolizador lento, intermedio, normal, rápido o ultrarrápido? | **CPIC**                                         | Estandariza la traducción del diplotipo a fenotipo                                      |
| Fenotipo → tratamiento       | ¿Debe cambiarse el fármaco o la dosis?                              | **CPIC** o **DPWG**                              | Ofrece recomendaciones clínicas gen–fármaco                                             |
| Validación clínica           | ¿El resultado es suficientemente robusto para reportarse?           | AMP/CAP, normas regulatorias y validación local  | Cobertura, precisión, CNV, fase, controles y limitaciones                               |
| Implementación computacional | ¿Cómo automatizar desde VCF hasta recomendación?                    | **PharmCAT/ClinPGx**                             | Anotación, asignación de diplotipo y traducción clínica                                 |

CPIC aclara que sus guías responden principalmente a cómo utilizar un resultado genético que ya está disponible, no necesariamente a decidir si debe solicitarse la prueba.

# 1. AMP: qué variantes debe incluir el análisis

Las recomendaciones de la Association for Molecular Pathology son probablemente lo más cercano a una guía de diseño bioinformático y analítico. Clasifican los alelos en:

Tier 1: deberían incluirse en todos los ensayos clínicos para ese gen.
Tier 2: alelos adicionales que pueden incorporarse según población, plataforma y propósito.

La selección considera frecuencia poblacional, efecto funcional, disponibilidad de materiales de referencia y viabilidad técnica. AMP ha publicado recomendaciones para genes como:

CYP2C19
CYP2C9
CYP2D6
TPMT
NUDT15
CYP3A4/CYP3A5
DPYD
genes relacionados con warfarina

Estas recomendaciones son esenciales porque un resultado como *1/*1 puede ser falso si el ensayo no interrogó alelos relevantes en la ancestría del paciente.

# 2. PharmVar: cómo construir los alelos estrella

PharmVar es el repositorio central de nomenclatura de farmacogenes. Define:

variantes que componen cada haplotipo;
alelos estrella y subalelos;
coordenadas y referencias;
evidencia de los alelos;
cambios de nomenclatura;
haplotipos de referencia.

No es una guía terapéutica. Es la fuente para responder:

¿Este conjunto de variantes corresponde a CYP2C19*2, CYP2D6*4 o CYP3A5*3?

PharmVar mantiene información sobre genes prioritarios como CYP2D6, CYP2C19, CYP2C9, DPYD, NUDT15, SLCO1B1, CYP3A5 y otros.

# 3. CPIC: del diplotipo al fenotipo y al tratamiento

CPIC proporciona tablas para traducir:

Variantes
   ↓
alelos estrella
   ↓
diplotipo
   ↓
función
   ↓
fenotipo metabolizador
   ↓
recomendación farmacológica

Ejemplo:

CYP2C19 *2/*2
→ dos alelos sin función
→ metabolizador lento
→ modificar selección o dosis según el fármaco

CPIC es una guía gen–fármaco. La recomendación cambia según el medicamento: el mismo fenotipo de CYP2C19 no se interpreta igual para clopidogrel, voriconazol o inhibidores de bomba de protones.

# 4. DPWG

El Dutch Pharmacogenetics Working Group también publica recomendaciones gen–fármaco. Puede diferir de CPIC en:

umbral de evidencia;
indicación de pruebas preemptivas;
clasificación fenotípica;
ajustes de dosis;
alternativa terapéutica.

Revisar CPIC y DPWG en paralelo -->  discrepancia y la fecha de actualización.

# 5. PharmCAT: interpretación computacional

Para una guía verdaderamente bioinformática, incluiría PharmCAT, porque permite procesar información genómica y generar:

llamados de alelos;
diplotipos;
fenotipos;
recomendaciones basadas en CPIC.

Sin embargo, no debe tratarse como una caja negra. La guía debe explicar:

versión del genoma;
normalización del VCF;
variantes ausentes;
genotipos no llamados;
fase;
cobertura;
CNV;
genes que requieren métodos especiales;
versión de PharmVar y CPIC utilizada.

ClinPGx integra actualmente recursos de PharmGKB, CPIC y PharmCAT.

# El punto crítico: genes técnicamente complejos
### CYP2D6

Es el ejemplo clásico de por qué un VCF convencional puede ser insuficiente. Deben evaluarse:

SNV e indels;
deleción completa, como *5;
duplicaciones y multiplicaciones;
número de copias;
híbridos CYP2D6–CYP2D7;
conversiones génicas;
fase;
qué alelo está duplicado.

Un resultado CYP2D6 *1/*4 no equivale a *1xN/*4. La duplicación puede cambiar el activity score y el fenotipo.

### HLA-A y HLA-B

Genes como HLA-B*57:01, HLA-B*15:02 y HLA-A*31:01 requieren tipificación alélica de alta resolución. No deben interpretarse únicamente mediante un SNP marcador sin validar que el marcador sea adecuado para la población.

### G6PD

No basta con identificar una variante. Deben considerarse:

sexo cromosómico;
hemicigosis;
heterocigosis;
fase;
inactivación del X;
posible discordancia entre genotipo y actividad enzimática.

### CYP2C9, CYP2C19, TPMT, NUDT15 y DPYD

Los paneles limitados pueden perder variantes poco frecuentes o específicas de ancestría. Un llamado por defecto de *1 significa con frecuencia:

“No se identificaron las variantes interrogadas”

y no necesariamente:

“El alelo fue secuenciado completamente y se confirmó como función normal”.

# Qué debe revisar una guía bioinformática de PGx

# 1. Definir el alcance
Gen específico, panel PGx, exoma o genoma.
Uso clínico o investigación.
Población y ancestría.
Fármacos que se informarán.
Versiones de referencia y nomenclatura.

# 2. Control de calidad
Cobertura por posición clínicamente relevante.
Calidad de base y genotipo.
Balance alélico.
Strand bias.
Mapeabilidad.
Homología con pseudogenes.
Número de copias.
Contaminación y concordancia de muestra.
Regiones no evaluables.

# 3. Normalización
Ensamble GRCh37 o GRCh38.
Representación izquierda de indels.
Descomposición de multialélicos.
Normalización de REF/ALT.
Identificadores PharmVar y dbSNP.
Transcrito y coordenadas correctas.

# 4. Asignación haplotípica
Variantes definitorias.
Cis/trans.
Fase directa o inferida.
Alelos ambiguos.
Subalelos.
CNV e híbridos.
No asignar *1 automáticamente por exclusión sin declarar limitaciones.

# 5. Traducción del diplotipo
Función de cada alelo.
Activity score, cuando aplica.
Fenotipo estandarizado.
Fenotipo indeterminado cuando existe ambigüedad.
Diferenciar genotipo de fenoconversión por medicamentos, enfermedad o función orgánica.

# 6. Recomendación clínica
CPIC.
DPWG.
Etiqueta regulatoria, cuando corresponda.
Fármaco y contexto clínico.
Evidencia y fuerza de recomendación.
Fecha y versión.

# 7. Reporte

Debe incluir:
gen y diplotipo;
variantes detectadas;
método;
cobertura;
número de copias;
fenotipo predicho;
recomendación gen–fármaco;
limitaciones;
guía y versión;
advertencia sobre fenoconversión;
resultados potencialmente accionables futuros.
