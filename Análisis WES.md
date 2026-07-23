# Flujo de trabajo
Pipeline

FASTQ
↓
QC (control de calidad)
↓
Alineamiento
↓
BAM / CRAM
↓
Recalibración
↓
Variant Calling - llamado de SNV e indels
↓
VCF
↓
Anotación
↓
Priorización
↓
Clasificación
↓
Interpretación
↓
Reporte

La priorización se concentra principalmente en:

regiones codificantes; sitios de splicing cercanos; SNV e indels; algunos CNV, si el pipeline los analiza; genes asociados con el fenotipo.

# Herramientas
FastQC
BWA
Samtools
Picard
GATK
DeepVariant
VEP
ANNOVAR
SnpEff
bcftools

# Controles de calidad
Coverage
Depth
Ti/Tv
Duplicados
Contaminación

Call rate

Limitaciones
