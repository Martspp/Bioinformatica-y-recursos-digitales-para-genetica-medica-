# 1. Introducción
¿Qué es la interpretación de variantes?
¿Por qué es importante?
Clasificación de variantes
Bases de datos
Flujo general de interpretación


# 2. ¿Qué guía debo utilizar?
| Tipo de variante          | Guía principal            | Guías complementarias       | Comentarios                           |
| ------------------------- | ------------------------- | --------------------------- | ------------------------------------- |
| SNV                       | ACMG/AMP 2015 + ACGS 2024 | ClinGen SVI                 | Guía estándar                         |
| Indels pequeños (<50 bp)  | ACMG/AMP                  | PVS1 ClinGen                | Igual que SNV                         |
| Deleción intragénica      | ACMG SNV                  | PVS1                        | Se interpreta como pérdida de función |
| Duplicación intragénica   | ACMG SNV                  | PVS1                        | Depende del marco de lectura          |
| CNV (>50 bp)              | ACMG/ClinGen CNV 2020     | ACGS 2024                   | Sistema por puntos                    |
| CNV detectado por WGS     | ACMG CNV                  | Evidencia técnica adicional | Requiere validar calidad              |
| Variantes no codificantes | Ellingford 2022           | ClinGen                     | Evidencia limitada                    |
| Expansiones repetidas     | Guías específicas         | ACMG cuando aplica          | No usar ACMG clásico                  |
| Variantes mitocondriales  | Mitochondrial ACMG        | MSeqDR                      | Heteroplasmia                         |
| Alelos de riesgo          | ACGS 2024                 | GWAS                        | No clasifican igual                   |
| Variantes hipomórficas    | ACGS 2024                 | Gene-specific               | Considerar contexto                   |
| Penetrancia reducida      | ACGS 2024                 | ClinGen                     | Contexto clínico                      |

# 3. ¿Qué base de datos debo revisar?
| Tipo         | Bases principales        |
| ------------ | ------------------------ |
| SNV          | ClinVar, gnomAD          |
| CNV          | DECIPHER, ClinGen Dosage |
| SV           | gnomAD SV                |
| Repetidos    | STRipy                   |
| Mitocondrial | MITOMAP                  |
| Splicing     | SpliceAI                 |
| Conservación | UCSC                     |
| Expresión    | GTEx                     |

# 4. ¿Qué herrramienta bioinformática debo utilizar?
| Variante | Herramientas               |
| -------- | -------------------------- |
| Missense | REVEL, AlphaMissense, CADD |
| Splicing | SpliceAI                   |
| CNV      | AnnotSV                    |
| SV       | Manta                      |
| WGS      | IGV                        |

# 5. ¿Qué debo leer?
| Si quiero aprender... | Leer            |
| --------------------- | --------------- |
| SNV                   | ACMG 2015       |
| Adaptaciones UK       | ACGS 2024       |
| CNV                   | Riggs 2020      |
| PVS1                  | ClinGen SVI     |
| PM3                   | ClinGen SVI     |
| De novo               | PS2/PM6         |
| No codificantes       | Ellingford 2022 |
| Dosificación          | ClinGen Dosage  |
| Cáncer                | CanVIG          |
| Gene-specific         | VCEP            |

# 6. Rutas de aprendizaje
| Nivel            | Tema                                       | Objetivo                                                   | Lecturas recomendadas                                             |
| ---------------- | ------------------------------------------ | ---------------------------------------------------------- | ----------------------------------------------------------------- |
| 🟢 Básico        | ¿Qué es una variante?                      | Comprender la nomenclatura y la clasificación general      | ACMG/AMP 2015 (introducción), GeneReviews sobre pruebas genéticas |
| 🟢 Básico        | Interpretación de SNV/indels               | Aplicar los criterios ACMG/AMP                             | ACMG/AMP 2015 + ACGS 2024                                         |
| 🟡 Intermedio    | Criterios específicos (PVS1, PS2/PM6, PM3) | Saber cuándo y cómo modificar la fuerza de la evidencia    | Recomendaciones ClinGen SVI correspondientes                      |
| 🟡 Intermedio    | Interpretación de CNV                      | Clasificar deleciones y duplicaciones constitucionales     | ACMG/ClinGen CNV 2020 (Riggs et al.) + ACGS 2024                  |
| 🟠 Avanzado      | CNV detectados por WGS                     | Integrar evidencia técnica y clínica para SV/CNV en genoma | ACGS 2024 + documentación de pipelines (DRAGEN/Manta/Canvas)      |
| 🟠 Avanzado      | Variantes no codificantes y splicing       | Interpretar variantes fuera de regiones codificantes       | Ellingford et al. 2022 + ClinGen SVI                              |
| 🔴 Especializado | Guías específicas por gen/enfermedad       | Aplicar criterios refinados para genes concretos           | VCEP (ClinGen), CanVIG, recomendaciones específicas de cada gen   |


