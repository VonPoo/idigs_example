# Here's an iDIGs Panel Design example.

Our aim was to screen the breeds we owned against the iDIGs database of variety markers, the breeds we have here are An Qing, BanNa Minipig, Jin Hua, we wanted to distinguish them from American_Feral, BaMaXiang, BaoShan's specific markers.

Upload Breeds Information: An Qing, BanNa Minipig, Jin Hua.

Select Breeds Information: American_Feral, BaMaXiang, BaoShan.

## Upload data generating

Here I am using WGS data, which is hardly upload. Thus, I download [markerID](http://alphaindex.zju.edu.cn/ALPHADB/data20220604/miaojian/IPGS.zip) and only extract overlapped markers to upload. 

First you need to prepare a ***cluster.txt*** in the following format:

the first column is the family name, the second column is the individual name, and the third column is the species.

```txt
0	SAMN17783368	AQ
0	SAMN17783369	AQ
0	SAMN17783371	AQ
0	SAMN17783372	AQ
0	SAMN17783373	AQ
0	SAMN17783374	AQ
0	SAMN17783376	AQ
0	SAMN17783377	AQ
0	SAMN17783378	AQ
0	SAMN17783379	AQ
0	SAMN17783380	AQ
0	SAMN17783381	AQ
0	SAMN17783382	AQ
0	SAMN17783384	AQ
0	SAMN17783385	AQ
0	BNM2417S1	BNM
0	BNM2422S1	BNM
0	BNM2489P1	BNM
0	BNM2574T1	BNM
0	BNM2575T1	BNM
0	BNM2636A3	BNM
0	BNM2643D1	BNM
0	BNM2653Q1	BNM
0	BNM2667P1	BNM
0	BNM2700Q1	BNM
0	BNM2870F1	BNM
0	BNM2887F5	BNM
0	BNM9075L1	BNM
0	BNM9183B1	BNM
0	BNM9355F5	BNM
0	JH_1_26	JH
0	JH_1_27	JH
0	JH_1_28	JH
0	JH_1_29	JH
0	JH_1_3	JH
0	JH_1_30	JH
0	JH_1_31	JH
0	JH_1_32	JH
0	JH_1_33	JH
0	JH_1_34	JH
0	JH_1_35	JH
0	JH_1_36	JH
0	JH_1_37	JH
0	JH_1_38	JH
0	JH_1_39	JH
```

Next, the relevant commands are as follows:

``` Linux
chmod +x MakeSNPidL

# Normalize your markerID in bim file and copy files
MakeSNPidL AQ_BNM_JH.bim AQ_BNM_JH.tmp.bim
cp AQ_BNM_JH.bed AQ_BNM_JH.tmp.bed
cp AQ_BNM_JH.fam AQ_BNM_JH.tmp.fam

# extract overlapped SNPs, this example uses PLINK version 1.9
plink --bfile AQ_BNM_JH.tmp --extract MarkerID_11.txt --make-bed --out AQ_BNM_JH_upload

# Calculating Allele Frequency Report
plink --bfile AQ_BNM_JH_upload --freq --allow-extra-chr --within cluster.txt --out AQ_BNM_JH
```

Now we have generated the files required for upload i.e. *.bim* & *.frq.strat*.

## Step1: Select version of reference genome

Here we have chosen the ***Sus scrofa*** reference genome version 11.1.

<img src="C:\Users\fengbo\Pictures\Screenshots\step1.png" alt="Step1" title="Step1" style="zoom:50%;" />

## Step2: Select number of markers

Here we have chosen the number of markers to be 50.

<img src="C:\Users\fengbo\Pictures\Screenshots\step2.png" alt="Step2" title="Step2" style="zoom:50%;" />

## Step3: Choose reference breeds

The reference Breeds we have chosen here are American_Feral, BaMaXiang, BaoShan.

<img src="C:\Users\fengbo\Pictures\Screenshots\step3.png" alt="Step3" style="zoom:50%;" />

## Step4: Upload the above generated files

First upload *AQ_BNM_JH.bim* file, then upload *AQ_BNM_JH.frq.strat* file

<img src="C:\Users\fengbo\Pictures\Screenshots\step4.png" alt="Step4" style="zoom:50%;" />

## Step5: Fill in your email address and submit the task

After completing these steps, about a cup of coffee time, the platform will be screened out of the 50 markers in ***html*** format sent to your mailbox, please pay attention to check.

## Result: The format of the outcome document and report is as follows

<img src="C:\Users\fengbo\Pictures\Screenshots\step5.png" alt="Step5" style="zoom:75%;" />

<img src="C:\Users\fengbo\Pictures\Screenshots\result.png" alt="Report" style="zoom:50%;" />
