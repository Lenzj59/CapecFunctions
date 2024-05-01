# CapecFunctions
A Program using CAPEC and CWEs with code2vec to obtain Java and Python functions that are subject to attack according to CAPEC.



## Java
javaMain.py does the majority of the processing. It takes in many inputs and outputs an excel file with an example function for each CAPEC (616 total) \
Inputs: \
cwe_descrips.json - This contains the CWE descriptions for each CWE from the MITRE website. It has been processed for relative information by cwe_descrips.py. \
score_test(capec2cwe[original+weighted_sbert]).json - This contains the mappings from CAPEC to CWE and their relative scores provided by Nick. The top 5 CWEs are used for each CAPEC. \ 
cleanoutput4.txt - This file contains each function name provided by running code2vec on the source code, followed by their original function name for later lookup. \
tokens.txt - This file contains the tokens provided by code2vec, and is used to get rid of filler words e.g "gives". \
javaFullMethods.txt - This file contains the every source code function used. It was retrieved through the files of the java-large dataset which contains 9000 github projects. \
\
javaMain.py uses a word2vec model to take the cwe descriptions and convert them to function names. This training includes the tokens given by code2vec to act as an input, and the relative function names from code2vec to act as an output. The model is trained in javatrainmodel.py and is saved in word2vec.model \
\
javaMain.py begins with retrieving the top 5 CWEs for a CAPEC and retrieving their descriptions along with extended descriptions. It then removes stop and filler words from the descriptions. It finds the most similar function match based on description. It then searches for it in cleanoutput4. If found, it finds and retrieves the function form javaFullMethods. If not found, it continues to next iteration.

## Python
pyMain.py is very similar to javaMain.py pyMain.py does the majority of the processing. It takes in many inputs and outputs an excel file with an example function for each CAPEC (616 total) \
Inputs: \
cwe_descrips.json - This contains the CWE descriptions for each CWE from the MITRE website. It has been processed for relative information by cwe_descrips.py. \
score_test(capec2cwe[original+weighted_sbert]).json - This contains the mappings from CAPEC to CWE and their relative scores provided by Nick. The top 5 CWEs are used for each CAPEC. \ 
pycleanoutput4.txt - This file contains each function name provided by running code2vec on the source code, followed by their original function name for later lookup. \
tokens.txt - This file contains the tokens provided by code2vec, and is used to get rid of filler words e.g "gives". \
pyFullMethods.txt - This file contains the every source code function used. It was retrieved through the files of the java-large dataset which contains 9000 github projects. \
\
pyMain.py uses a word2vec model to take the cwe descriptions and convert them to function names. This training includes the tokens given by code2vec to act as an input, and the relative function names from code2vec to act as an output. The model is trained in pytrainmodel.py and is saved in pyword2vec.model \
\
pyMain.py begins with retrieving the top 5 CWEs for a CAPEC and retrieving their descriptions along with extended descriptions. It then removes stop and filler words from the descriptions. It finds the most similar function match based on description. It then searches for it in cleanoutput4. If found, it finds and retrieves the function form pyFullMethods. If not found, it continues to next iteration.

## Extras
top5.py - matches each CAPEC with top 5 matching CWEs

