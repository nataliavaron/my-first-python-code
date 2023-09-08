# my-first-python-code
This code is an experiment, designed to search for genes in common and different between genomes in a basic way.
# Genoma de Streptococcus pneumoniae (extraccion de genes)
import sys

sequence_file= "Spneumoniae.gb"

spneumoniae_gene_set = set()
spneumoniae_gene_list = []

#lectura de la secuencia
with open(sequence_file) as file:
    for line in file:
        line = line.rstrip()

        # extraccion de informacion de interes del formato
        if "/gene=" in line:
            line = line.strip()
            gene = line[7:-1]
            print(line)
            print(gene)

            # almacenar y registrar los nombres de los genes extraídos
            spneumoniae_gene_set.add(gene)
            spneumoniae_gene_list.append(gene)
pass

# genoma de Streptococcus mitis (extraccion de genes)

sequence_file= "Smitis.gb"

smitis_gene_set = set()
smitis_gene_list = []

#lectura de la secuencia
with open(sequence_file) as file:
    for line in file:
        line = line.rstrip()

        # extraccion de informacion de interes del formato
        if "/gene=" in line:
            line = line.strip()
            gene = line[7:-1]
            print(line)
            print(gene)

            # almacenar y registrar los nombres de los genes extraídos
            smitis_gene_set.add(gene)
            smitis_gene_list.append(gene)

pass

# interseccion de genes de las bacterias (encontrar aquelos genes en comun entre los genomas)

genes_comunes = spneumoniae_gene_set.intersection(smitis_gene_set)
print("Genes comunes entre Spneumoniae y smitis")
for gene in genes_comunes:
    print(gene)

    # Nombre del archivo de salida
    archivo_salida = "genes_comunes.txt"

    # Redirigir la salida estándar a un archivo
    sys.stdout = open(archivo_salida, "w")

    print("Genes comunes entre Spneumoniae y smitis")
    for gene in genes_comunes:
        print(gene)

    print(f"Genes comunes guardados en {archivo_salida}")

pass

# Genes diferentes entre las bacterias (por medio de diferencia de conjuntos)
genes_diferentes_spneumoniae = spneumoniae_gene_set.difference(smitis_gene_set)

# Nombre del archivo de salida
archivo_genes_diferentes_spneumoniae = "genes_diferentes_spneumoniae.txt"

# Redirigir la salida estándar a un archivo
sys.stdout = open(archivo_genes_diferentes_spneumoniae, "w")
print("Genes diferentes en Streptococcus pneumoniae")
for gene in genes_diferentes_spneumoniae:
    print(gene)


print(f"Genes diferentes en Streptococcus pneumoniae guardados en {archivo_genes_diferentes_spneumoniae}")

pass

# Genes diferentes entre las bacterias (por medio de diferencia de conjuntos)
genes_diferentes_smitis = smitis_gene_set.difference(spneumoniae_gene_set)

# Nombre del archivo de salida
archivo_genes_diferentes_smitis = "genes_diferentes_smitis.txt"

# Redirigir la salida estándar a un archivo
sys.stdout = open(archivo_genes_diferentes_smitis, "w")
print("Genes diferentes en Streptococcus mitis")
for gene in genes_diferentes_smitis:
    print(gene)

print(f"Genes diferentes en Streptococcus mitis guardados en {archivo_genes_diferentes_smitis}")

pass

