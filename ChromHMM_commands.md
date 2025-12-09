# ChromHMM Commands

# Altering K values:

## Human Data

> ### Binarize Bed
```
java -mx80000M -jar ChromHMM.jar BinarizeBed -peaks hg19.txt peaks_dir/ cellmarkfile.tsv binary/
```
> ### Learn Model
```
for K in {1..25}
do
    java -mx80000M -jar ChromHMM.jar LearnModel binary/ model_${K} ${K} hg19 > model_${K}.output.txt
done
```
## Mouse data
> ### Binarize Bam
```
java -mx80000M -jar ChromHMM.jar BinarizeBam mm10.txt bams/ cellmarkfile.tsv binary/
```
> ### Learn Model
```
for K in {1..25}
do
    java -mx80000M -jar ChromHMM.jar LearnModel binary/ learnmodel_${K}/ ${K} mm10 > learnmodel_${K}.log
done
```

# Altering bin values:
## Human Data
> ### Binarize Bed
```
for B in {100,200,500,1000}
do 
    java -mx80000M -jar ChromHMM.jar BinarizeBed -peaks -b ${B} hg19.txt peaks_dir/ binary_${B}
done
```
> ### Learn Model
```
for B in {100,200,500,1000}
do 
    java -mx80000M -jar ChromHMM.jar LearnModel -b${B} binary_${B} model_${B}_bin 15 hg19 > ${B}_bin_model.output.txt
done
```

## Mouse data
> ### Binarize Bam
```
for B in {100,200,500,1000}
do 
    java -mx80000M -jar ChromHMM.jar BinarizeBam -b ${B} mm10.txt bams/ binary_${B}
done
```

> ### Learn Model
```
for B in {100,200,500,1000}
do 
    java -mx80000M -jar ChromHMM.jar LearnModel -b${B} binary_${B} model_${B}_bin 18 mm10 > ${B}_bin_model.output.txt
done
```

# CompareModels
```
java -mx80000M -jar ChromHMM.jar CompareModels emissions_15.txt comparedir/ 15_comparison
```