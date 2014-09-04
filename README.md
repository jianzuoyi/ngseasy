NGSeasy v1.0
===================

[Dockerized](https://www.docker.com/) and [Virtulaized](https://www.virtualbox.org/) ngs pipeline and tool-box.  

As a multi-component system, NGS pipeline setup is traditionally heavy on 
configuration. Our idea is to provide this in a simple encapsulated container. 
Users also typically wish to configure their own environments and run the 
pipeline on a wide range of hardware (workstations to clusters to cloud), being 
able to stand-up a pipeline with minimal fuss is made straightforward with this 
container.  

**With NGSeasy you can now have full suite of NGS tools up and running on any high end workstation in an afternoon**

******

<a href="https://twitter.com/share" class="twitter-share-button">Tweet</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>

### Authors
- Amos Folarin <amosfolarin@gmail.com>  
<a href="http://www.linkedin.com/pub/amos-folarin/34/b06/978">
<img src="http://www.linkedin.com/img/webpromo/btn_viewmy_160x33.png" width="160" height="33" alt="View Amos's profile on LinkedIn">
</a>

- Stephen J Newhouse <stephen.j.newhouse@gmail.com>  
<a href="http://uk.linkedin.com/pub/dr-stephen-newhouse/29/89a/11a">
<img src="http://www.linkedin.com/img/webpromo/btn_viewmy_160x33.png" width="160" height="33" alt="View Steve's profile on LinkedIn">
</a>

Lets us know if you want other tools added to NGSeasy  

## Table of Contents
[NOTICE TO USERS](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#notice-to-users-of-the-container-image-or-vm)  

[Software requiring registration](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#software-composing-the-pipeline-requiring-registration)  

[Overview of Pipeline Components](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#overview-of-pipeline-components)  

[NGS Tools](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#the-tools-included-are-as-follows--)  

[Dockerised NGSEASY set up](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#dockerised-ngseasy)  

[Installing Docker](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#installing-docker)  

[Getting the Dockerised NGSEASY Pipeline](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#getting-the-dockerised-ngseasy-pipeline)  

[Running the Dockerised NGSEASY Pipeline](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#running-the-dockerised-ngseasy-pipeline)  

[Local Machine Set up](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#local-machine-set-up)  

[NGSEASY-VM : An NGS Tool Box](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngseasy-vm--an-ngs-tool-box)  

[Installing Oracle VirtualBox](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#installing-oracle-virtualbox)  

[Getting the ngseasy-vm](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#getting-the-ngseasy-vm)  

[Installing the ngseasy-vm](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#installing-the-ngseasy-vm)  

******

# NOTICE TO USERS OF THE CONTAINER IMAGE OR VM

While the software used to build the image is composed of free software versions
some of the software has restrictions on use particularly for commercial 
purposes. Therefore if you wish to use this for commercial purposes, then you 
leagally have to approach the owners of the various components yourself!  

This pipeline uses a number of pieces of software which require registration. 
By using this you are agreeing to observe the Terms and Conditions of the 
relevant pieces of software that compose this pipeline.  

# Software composing the pipeline requiring registration

If you want to build the image from the Dockerfile then you need to get your 
own versions of (below) in the build directory:

   * novoalign http://www.novocraft.com/
   * Stampy http://www.well.ox.ac.uk/project-stampy
   * GATK https://www.broadinstitute.org/gatk/
   * ANNOVAR http://www.openbioinformatics.org/annovar/

[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******

Overview of Pipeline Components
================================
The basic pipeline contains all the basic tools needed for manipulation and 
quality control of raw fastq files (ILLUMINA focused), SAM/BAM manipulation,
alignment, cleaning (based on GATK best practises [ADD LINK]) and first pass
variant discovery. Separate containers are provided for indepth variant annotation,
structural variant calling, basic reporting and visualisations.  

![ngsEASY](figs/ngsEASY_pipeline_visualisation.png "Dockerized NGS Pipeline")


# The Tools included are as follows :- 

### Fastq manipulation
- FASTQC
- SEQTK
- TRIMMOMATIC
- FASTX TOOLKIT

### Alignmnet
- BWA
- BOWTIE2
- STAMPY
- NOVOALIGN [FULL VERSION NOT AVAILABLE FOR PUBLIC USE]

### SAM/BAM Processing
- GATK
- PICARDTOOLS
- SAMTOOLS

### MISC
- BEDTOOLS
- VCFTOOLS
- BCFTOOLS

### VARIANT CALLING
- GATK
- SAMTOOLS/BCFTOOLS
- FREEBAYES
- PLATYPUS

### VARIANT ANNOTATION
- ANNOVAR
- SNPEFF
- VEP

### CNV/Structural Variant CALLING
- lumpy
- delly
- m-HMM
- cn.MOPS
- ExomeDepth

[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******

##### To Add 
- SegSeq
- MuTect
- MutSig

******

Dockerised NGSEASY
==========================
![docker](figs/Docker_container_engine_logo.png "Docker")  

## Installing Docker

Follow the simple instructions in the links provided below  

- [Mac](https://docs.docker.com/installation/mac/)  
- [Windows](https://docs.docker.com/installation/windows/)
- [Ubuntu](https://docs.docker.com/installation/ubuntulinux/)

A full set of instructions for multiple operating systems are available on the [Docker website](https://docs.docker.com/installation/).

## Getting the Dockerised NGSEASY Pipeline

Available NGSeasy images at [afolarin/ Docker Hub](https://hub.docker.com/u/afolarin/) and [snewhouse/ Docker Hub](https://hub.docker.com/u/snewhouse/)

#### Getting the main NGSeasy suite of tools

[snewhouse/ngseasy-alignment-public:v1.2](https://registry.hub.docker.com/u/snewhouse/ngseasy-alignment-public/)

This is a large image (4.989 GB) containing all the tools needed to go from raw ``.fastq`` files to aligned ``.BAM`` to SNP and small INDEL variant calls ``.vcf`` .

```bash
sudo docker pull snewhouse/ngseasy-alignment-public:v1.2
```

#### Getting All NGSeasy images

```bash
#!/bin/bash
# get ngseasy from DockerHub
repo='snewhouse'

for i in alignment-public:v1.2 \
fastqc:v1.0 \
var-callers:v1.1 \
var-anno:v1.1 \
sv-delly:v1.1 \
sv-lumpy:v1.1 \
sv-mhmm:v1.0 \
sv-cnmops:v1.0 \
sv-exomedepth:v1.0 \
bedtools:v1.0 \
bwa:v1.0 \
bowtie2:v1.0 \
gatk:v1.0 \
picard:v1.0 \
samtools:v1.0 \
stampy:v1.0 \
vcftools:v1.0 \
freebayes:v1.0 \
platypus:v1.0;do
sudo docker pull ${repo}/ngseasy-${i};
done
```

## Local Machine Set up

### Download NGSeasy resources 

This is a %6GB ``ngseasy_resources.tar.gz`` file containing :-  

- ``reference_genomes_b37.tgz`` b37 reference genomes indexed for use with all provided aligners (BWA, Bowtie2, Stampy, Novoalign) and annotation bed files for use with pipeline scripts
- ``humandb.tgz`` ANNOVAR humandb 
- ``gatk_resources.tar.gz`` gatk resources bundle
- ``fastq_example.tgz`` Example 75bp PE Illumina Whole Exome Sequence fastq data for **NA12878**

**In Linux**

```bash
tar -xfv ngseasy_resources.tar.gz
cp -rf ngseasy_resources/reference_genomes_b37 ~/reference_genomes_b37
cp -rf  ngseasy_resources/gatk_resources ~/humandb
cp -rf  ngseasy_resources/gatk_resources ~/gatk_resources
cp -rf  ngseasy_resources/fastq_example ~/fastq_raw
```

**On your local machine, ensure the following directories exist:-**

- ``fastq_raw`` [to hold all incoming raw fastq files]
- ``ngs_projects`` [out put directory for all ngs projects]
- ``reference_genomes_b37`` [get from URL and unpack. NB: XXX GB!]
- ``gatk_resources`` [vcf and annotation files used by GATK]
- ``humandb`` [annovar databases]

These folders are required by pipeline as they are hardcoded in the NGSeasy scripts. I would recommend installing these in your ``HOME`` directory.

### Getting the GATK Resources Bundle for yourself

[What's in the resource bundle and how can I get it?](https://www.broadinstitute.org/gatk/guide/article.php?id=1213)

```bash
## FTP Login Details
location: ftp.broadinstitute.org
username: gsapubftp-anonymous
password: <blank>
```
I would recommend using a separate program like [FileZilla](https://filezilla-project.org/), which will make it much easier for you to set up and manage your file transfers

**Path to gatk_resources.tgz**
```
ftp://ftp.broadinstitute.org/distribution/gsa/gatk_resources.tgz
```
**Contents**
- 1000G_omni2.5.b37.vcf  
- 1000G_omni2.5.b37.vcf.idx  
- 1000G_phase1.indels.b37.vcf  
- 1000G_phase1.indels.b37.vcf.idx  
- 1000G_phase1.snps.high_confidence.b37.vcf  
- 1000G_phase1.snps.high_confidence.b37.vcf.idx  
- CEUTrio.HiSeq.WGS.b37.bestPractices.b37.vcf  
- CEUTrio.HiSeq.WGS.b37.bestPractices.b37.vcf.idx  
- CEUTrio.HiSeq.WGS.b37.NA12878.vcf  
- CEUTrio.HiSeq.WGS.b37.NA12878.vcf.idx  
- dbsnp_138.b37.excluding_sites_after_129.vcf  
- dbsnp_138.b37.excluding_sites_after_129.vcf.idx  
- dbsnp_138.b37.vcf  
- dbsnp_138.b37.vcf.idx  
- hapmap_3.3.b37.vcf  
- hapmap_3.3.b37.vcf.idx  
- Mills_and_1000G_gold_standard.indels.b37.vcf  
- Mills_and_1000G_gold_standard.indels.b37.vcf.idx  
- NA12878.HiSeq.WGS.bwa.cleaned.raw.subset.b37.sites.vcf  
- NA12878.HiSeq.WGS.bwa.cleaned.raw.subset.b37.sites.vcf.idx  
- NA12878.HiSeq.WGS.bwa.cleaned.raw.subset.b37.vcf  
- NA12878.HiSeq.WGS.bwa.cleaned.raw.subset.b37.vcf.idx  
- NA12878.knowledgebase.snapshot.20131119.b37.vcf  
- NA12878.knowledgebase.snapshot.20131119.b37.vcf.idx  


## Get NGSeasy Scripts

```bash
git clone XXXXXX
```



**the scripts will eventually be bundled with each docker image**
[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

**********

Running the Dockerised NGSEASY Pipeline
==========================================

```bash
sudo docker run -d -P \
-v ~/fastq_raw:/home/pipeman/fastq_raw \
-v ~/reference_geneomes:/usr/local/pipeman/reference_genomes \
-v ~/gatk_resources:/usr/local/pipeman/gatk_resources \
-v ~/ngs_projects:/home/pipeman/ngs_projects \
-v ~/ngseay_scripts:/usr/local/pipeman/ngseasy_scripts \
-u pipeman \
-t snewhouse/alignment-public:v1.2 /sbin/my_init -- bash run-ea-ngs.sh ngs.config
```

``-v`` used to mount host directories containing fastq, reference genomes, gatk resources and project output.
The ``-u pipeman`` ensures it is run using the ``pipeman`` user.

[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******

NGSEASY-VM : An NGS Tool Box
================================
![VirtualBox](figs/add-virtualbox.png "VirtualBox")  

A virtual machine based on [Ubuntu 14.04 LTS](http://www.ubuntu.com/desktop), containing all these [NGS Tools](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#the-tools-included-are-as-follows--) (and a few extras) is available. The virtual machine contains indexed reference genomes (b37) for all the installed aligners and the [GATK Resources Budle](https://www.broadinstitute.org/gatk/download).  

Using [VirtualBox](https://www.virtualbox.org/) and our NGSEASY-VM [ngseasy-vm-v1.0.vdi]() you can have a full suite of NGS tools up and running on any high end workstation in less than an hour.

## 1. Installing Oracle VirtualBox

The latest Oracle VM VirtualBox is available [here](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox)

Remember to install the latest [Oracle VM VirtualBox Extension Pack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

A full set of instructions are available here:-  

- [Oracle VirtualBox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)  
- [VirtualBox User Manual](http://download.virtualbox.org/virtualbox/UserManual.pdf)  
- [VirtualBox Installation Details](https://www.virtualbox.org/manual/ch02.html)  


## 2. Getting the ngseasy-vm

Download the ngseasy-vm [ngseasy-vm-v1.0.vdi]() and save this anywhere on your local machine.  

**NOTE:** This file is XXXGB in size.  

## 3. Installing the ngseasy-vm

Create a new virtual machine from the downloaded [ngseasy-vm-v1.0.vdi]().  

**Step 1.** Fire up VirtualBox and click **New**  
**Step 2.** The **Create Virtual Machine** window will appear  
**Step 3.** You will presented with 3 options that need to be set as  

> Name: **ngseasy**  
> Type: **Linux**  
> Version: **Ubuntu (64 bit)** 
 
**Step 4.** Click **Next** . This will take you to the **Memory Size** window  
**Step 5.** Select the amount of memmory (RAM) in megabytes to be allocated to the virtual machine (recommended 8GB). The size you 
allocate will depend on the available RAM on your machine. Adjust this vaule as needed. Click **Next**  
**Step 6.** This will take you to the **Hard drive** window. This is the important step. You will be presented with 3 options:-  

> Do not add a virtual hard drive  
> Create a virtual hard drive  
> Use an existing virtual hard drive file  

**Step 7.** Select **Use an existing virtual hard drive file**.   
**Step 8.** Click on the folder icon and point to the **ngseasy-vm.vdi** file.  
**Step 9.** Step  Click **Create**  

Once the new virtual machine is created, that virtual machine should fire up as expected 
and regardless of platform (I have tested this going from Linux to Linux, Linux to Windows, and Windows to Linux hosts).  

Before starting the virtual machine you can go to the **Settings** tab and alter the amount or RAM, CPUs assigned to the machine.
There is also the functionality to mount shared drives between the host OS and the virtual machine. In the **General** > **Advanced** tab,
ensure thet the **Shared Clipboard** and **Drang n Drop** are both set to **Bidirectional**.

[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******

Minimum Hardware Requirements
===============================
- 64 bit computer and operating system is recommended for more than 2 GB RAM
- 8GB RAM
- 8 Cores
- Minimum 100GB storage

[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******

```
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
[Back to The Begining](https://github.com/KHP-Informatics/ngs/blob/dev2/containerized/README.md#ngs-easy-v10)

******
