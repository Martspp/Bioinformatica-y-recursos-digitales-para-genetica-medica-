
El Comité de Nomenclatura de Variantes del HGVS (HVNC, https://hgvs-nomenclature.org/stable/) está autorizado por la Organización del Genoma Humano (HUGO, https://www.hugo-international.org/) , un grupo de trabajo del Comité de Estándares de Nomenclatura de HUGO , con el apoyo administrativo de la oficina de HUGO.

# Guía rápida de nomenclatura de variantes (HGVS)

> Basado en las recomendaciones de la Human Genome Variation Society (HGVS).

---

# ¿Qué es HGVS?

La **Human Genome Variation Society (HGVS)** establece un estándar internacional para describir variantes genéticas de forma precisa y consistente.

El objetivo es que cualquier laboratorio o investigador interprete exactamente la misma variante, independientemente de la plataforma utilizada.

---

# Estructura general

Una descripción HGVS tiene dos componentes principales:

```
<Referencia>:<Descripción de la variante>
```

Ejemplo:

```
NM_000059.4:c.7790G>A
```

* **NM_000059.4** → transcrito de referencia (RefSeq)
* **c.7790G>A** → variante descrita sobre la secuencia codificante

---

# Tipos de referencia

| Prefijo | Significado           | Ejemplo                    |
| ------- | --------------------- | -------------------------- |
| g.      | ADN genómico          | NC_000017.11:g.43071077A>G |
| c.      | ADN codificante (CDS) | NM_000059.4:c.7790G>A      |
| n.      | ARN no codificante    | NR_003287.2:n.125A>G       |
| r.      | ARN                   | r.76a>g                    |
| p.      | Proteína              | NP_000050.2:p.(Lys76Arg)   |
| m.      | ADN mitocondrial      | NC_012920.1:m.3243A>G      |

**Regla práctica:** En genética clínica, las descripciones más comunes son **g.**, **c.** y **p.**

---

# Referencias de secuencia

## RefSeq (NCBI)

Ejemplos:

```
NM_000546.6
```

Transcrito de ARNm.

```
NP_000537.3
```

Proteína.

```
NC_000017.11
```

Cromosoma completo.

---

## MANE

Siempre que sea posible, se recomienda utilizar los transcritos **MANE Select**, ya que armonizan las referencias entre RefSeq y Ensembl.

---

# Posiciones en nomenclatura c.

La numeración comienza en el nucleótido **A** del codón de inicio (ATG).

```
c.1
```

Corresponde a la A del ATG.

Ejemplo:

```
ATG GCT GAA...
↑
c.1
```

---

## Posiciones negativas

Antes del codón de inicio.

```
c.-35A>G
```

Variante 35 nucleótidos antes del ATG.

---

## Posiciones después del codón STOP

```
c.*15A>G
```

Variante 15 nucleótidos después del codón de terminación.

---

# Sustituciones

Formato:

```
Referencia > Alternativa
```

Ejemplo:

```
c.743G>A
```

Significa:

* En la posición 743
* La base de referencia es G
* Se sustituyó por A

---

# Deleciones

```
c.5266del
```

Eliminación de un nucleótido.

---

```
c.5266_5269del
```

Eliminación de varios nucleótidos consecutivos.

---

# Inserciones

```
c.100_101insA
```

Inserción de una adenina.

---

# Duplicaciones

```
c.68_69dup
```

Duplicación de la secuencia.

No debe escribirse como "ins".

---

# Delins (indel complejo)

Cuando una región se elimina y simultáneamente se inserta otra.

```
c.112_117delinsTG
```

---

# Inversiones

```
c.150_200inv
```

La región cambia de orientación.

---

# Variantes en sitios de splicing

Ejemplo:

```
c.519+1G>A
```

Primer nucleótido del intrón.

---

```
c.519+5G>A
```

Cinco nucleótidos dentro del intrón.

---

```
c.520-2A>G
```

Dos nucleótidos antes del siguiente exón.

---

# Variantes en proteína

Ejemplo:

```
p.Arg117His
```

Arginina → Histidina.

Abreviada:

```
p.R117H
```

---

## Nonsense

```
p.Arg97Ter
```

También puede encontrarse como:

```
p.Arg97*
```

---

## Frameshift

```
p.Leu818CysfsTer2
```

Significa:

* Cambio del marco de lectura
* Nuevo codón de paro dos aminoácidos después

---

## Sinónima

```
p.=
```

No cambia el aminoácido.

---

## Consecuencia incierta

```
p.?
```

No puede predecirse el efecto proteico.

---

# Ejemplo completo

```
NM_000546.6:c.743G>A
NP_000537.3:p.Arg248Gln
```

Interpretación:

* Transcrito RefSeq NM_000546.6
* Cambio G>A en la posición codificante 743
* Arginina reemplazada por glutamina en la posición 248

---

# Errores frecuentes

❌ Mezclar coordenadas genómicas con codificantes.

```
g.
```

≠

```
c.
```

---

❌ No indicar el transcrito utilizado.

Incorrecto:

```
c.743G>A
```

Correcto:

```
NM_000546.6:c.743G>A
```

---

❌ Usar un transcrito diferente al reportado por el laboratorio sin verificar que la numeración cambie.

---

❌ Confundir duplicaciones con inserciones.

```
dup
```

No es equivalente a

```
ins
```

---

❌ Reportar únicamente el cambio proteico.

Siempre que sea posible, incluir la variante a nivel de ADN y proteína.

---

# Recomendaciones para interpretación clínica

* Utilizar el transcrito reportado por el laboratorio o un transcrito MANE cuando esté disponible.
* Confirmar que la nomenclatura sea válida antes de buscar la variante en ClinVar, OMIM o PubMed.
* Verificar que la descripción HGVS corresponda al ensamblaje de referencia utilizado (GRCh37 o GRCh38).
* Recordar que una misma variante puede tener diferentes descripciones HGVS si cambia el transcrito de referencia.

---

# Recursos recomendados

* HGVS Nomenclature (https://hgvs-nomenclature.org/)
* MANE (Matched Annotation from NCBI and EMBL-EBI)
* RefSeq (NCBI)
* ClinVar
* VariantValidator
* Mutalyzer
