# KRAKEN TOOLS

## Alpha-Diversity Calculation:
$ python KrakenTools/DiversityTools/alpha_diversity.py \
-f bracken_outputs/SRR14143424.bracken -a BP

### What it does:
This command runs the alpha_diversity.py script from KrakenTools.
The -f flag specifies the input file, which is a '.bracken' file produced by Bracken.
The -a flag specifies the metric for calculating alpha diversity. Here, BP mean a specific type of alpha-diversity, like Shannon.

### Possible issues:
The path to the alpha_diversity.py script might be incorrect or missing execution permissions.
Ensure the input file (SRR14143424.bracken) exists in the specified location (bracken_outputs).
BP must be a valid metric recognized by the script. Check the documentation.

## Beta-Diversity Calculation

$ python KrakenTools/DiversityTools/beta_diversity.py -i \
bracken_outputs/SRR14092160.bracken bracken_outputs/SRR14092310.bracken \
bracken_outputs/SRR14143424.bracken --type bracken

### What it does:
Runs the beta_diversity.py script to calculate beta diversity.
-i specifies multiple input files for beta-diversity comparison.
--type bracken tells the script to expect .bracken files as input.

### Possible issues:
Make sure all listed .bracken files exist in the specified bracken_outputs folder.
The beta_diversity.py script may require specific parameters for --type bracken; verify compatibility.
If the file paths are long, ensure they're correctly quoted to avoid line-break issues.

## Generate Krona Plots

$ python KrakenTools/kreport2krona.py -r breports/SRR14143424.breport \
-o b_krona_txt/SRR14143424.b.krona.txt --no-intermediate-ranks
$ KronaScripts/ktImportText b_krona_txt/SRR14143424.b.krona.txt \
-o krona_html/SRR14143424.krona.html

### What it does:
Converts a .breport file (Kraken/Bracken output) into a Krona-compatible text file using kreport2krona.py.
-r specifies the input .breport file.
-o specifies the output file for the Krona-compatible text.
--no-intermediate-ranks excludes intermediate taxonomy ranks in the output.
Generates an interactive Krona HTML visualization from the text file using ktImportText.
The output file is stored in the krona_html directory.

### Possible issues:
Ensure kreport2krona.py and ktImportText are in the system PATH or their full paths are provided.
Check if the breports and b_krona_txt directories exist and have the necessary write permissions.
If ktImportText is not installed or accessible, it will fail.
The same process repeats for SRR14092160.breport and SRR14092310.breport.

