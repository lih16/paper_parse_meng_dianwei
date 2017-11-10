Sema4Var Project:

root /sc/orga/projects/chenr02a/Sema4Var

               |------  originaldata               
               |
root ----------|------  tools
               |
               |------  results

(I) Original data

	We place all the pdf files under originaldata/AllPDFPapers and fulltext. One hgmd file in 
	originaldata/hgmd, which is HGMD_2017_allmut.txt.

(II) tools

	To convert pdf files to TXT files, we used a tool named with PDF2TXT.jar, which is located 
	at tools. To use it, just run 'java -jar PDF2TXT.jar'. Please read our readme under tool. 

(III) results

	Summary of results:
	we collected 7970 pdf files. From them, 7542 pdf files were converted into TXT files. 428 
	pdf files were failed. In the end, 6420 TXT files were in database (see 6420pmid.txt).                            
	277 carrier gene.

	For the results, we currently have three parts. The folder categorization is empty so far.                     
	For PDF2TXTfiles, we place all the TXT files which are converted from pdf files. In fact,
	we ran our code two times, that's why you would see roundONEOUT and roundTWOOUT.                              

        In the middle of August, we reported our status to Rong. And in the mean time, we roughly
        analysed the reasons of failing to convert some of pdf files to TXT format.

	In textmining part, we carried out some research to see how many acc_num (in HGMD) were covered
	by our result. The rest of the document is about this part.                               
	
                                              

-------------------------------------------------------------------------------------------------
Inputfiles:
	allpdf_nonewline.csv
	HGMD_2017_allmut.txt	
-------------------------------------------------------------------------------------------------
Outputfile:
	result.csv
-------------------------------------------------------------------------------------------------
	
Columns of outputfile

	Field-name   	Value
	pmid 		15992519	
        acc_num		CM056358

Algorithm:
	We use two files as input files. The first is allpdf_nonewline.csv, and the second is 
	HGMD_2017_allmut.txt. We take the first file as "a" and the second file as "b".

	When a.pmid == b.pmid 
                 
    	           if (a.grounded matches b.hgvs) or
                      (a.grounded matches b.hgvsAll) or 
 		      (a.tool is "DBSNP") and (a.grounded matches b.dbsnp) 

                   then 
                      write(a.pmid, b.acc_num);

       Note: we handle 3-Letter and a.grounded starting with "?.". 

	
