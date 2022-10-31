## Grep
1. [Recursive searches](#recursivesearches)
2. [Match count](#matchcount)
3. [Printing additional lines](#printingmore)

## Recursive Searches

    ragalinapalaka@Ragalinas-MacBook-Pro technical % grep -r "bike" *
    biomed/1471-2458-2-11.txt:          several days after riding a motorbike through sewage
    government/Alcohol_Problems/Session3-PDF.txt:funded to change six behaviors among youth: not wearing bike
    government/Alcohol_Problems/Session3-PDF.txt:bike helmet use and a slightly larger change in seat belt use, but
    government/Media/man_on_national_team.txt:"Lico likes to be recognized as a biker, but I'm sure he's very

The ```grep -r``` command recursively searches through every subdirectory and file in the working directory. ```grep -r "bike" *``` gives the same results as ```grep "bike" technical/*/*.txt``` would, but with less room for error. 

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -r "brisk" *
    technical/government/Media/Survey.txt:law school, increases that have briskly outpaced inflation in any
    technical/plos/pmed.0010051.txt:        The patient had a brisk reticulocyte response. Her reticulocyte count rose from 0.36% to
    technical/plos/pmed.0010051.txt:        The brisk return of her WBC and platelet counts upon discontinuing carbamazepine, and
    technical/plos/pmed.0010051.txt:        her brisk reticulocytosis upon discontinuing sodium valproate, were both consistent with
    technical/biomed/1475-2891-2-1.txt:          min, i.e. walking briskly, cycling outdoor, swimming
    technical/biomed/1475-2891-2-1.txt:          >7 Kcal/ min, i.e. walking briskly uphill, long
    technical/biomed/1476-511X-2-3.txt:          calories 4-7 Kcal/ min, i.e. walking briskly, cycling
    technical/biomed/1476-511X-2-3.txt:          (expended calories >7 Kcal/ min, i.e. walking briskly

Essentially, ```grep -r "brisk" *``` traverses through every file in every sub directry to find and return every file that contains "brisk" in it. 

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -r "athletes" *   
    technical/plos/pmed.0020060.txt:        than—what?—some kind of snack food, some kind of energy chunk for genius triathletes”
    technical/plos/journal.pbio.0020348.txt:        athletes from different sports events. These studies revealed that successful endurance
    technical/plos/journal.pbio.0020348.txt:        athletes have relatively more ST than FT fibers in the trained musculature (Costill et al.
    technical/plos/journal.pbio.0020348.txt:        However, fiber type alone did not determine the performances of the elite athletes. For
    technical/plos/journal.pbio.0020348.txt:        example, two athletes with similar best times for the 42.2 km marathon distance

Similarly, here the same command is repeated, but it is not searching for "athletes". ```grep -r``` is particularly useful if the working directory has files and other subdirectories, since using ```*/*.txt``` or something similar may not be able to cover all file and subdirectory possibilities.

## Match Count

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -c "diversity" technical/*/*/dive
    rsity_priorities.txt
    44

```grep -c``` counts the number of times the pattern is matched instead of returning each instance. For example, "diversity" appeared 44 times in ```diversity_priorities.txt```.

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -c "climate" technical/*/Env_Prot_Agen/*.txt
    technical/government/Env_Prot_Agen/1-3_meth_901.txt:0
    technical/government/Env_Prot_Agen/atx1-6.txt:2
    technical/government/Env_Prot_Agen/bill.txt:0
    technical/government/Env_Prot_Agen/ctf1-6.txt:0
    technical/government/Env_Prot_Agen/ctf7-10.txt:0
    technical/government/Env_Prot_Agen/ctm4-10.txt:1
    technical/government/Env_Prot_Agen/final.txt:10
    technical/government/Env_Prot_Agen/jeffordslieberm.txt:3
    technical/government/Env_Prot_Agen/multi102902.txt:0
    technical/government/Env_Prot_Agen/nov1.txt:6
    technical/government/Env_Prot_Agen/ro_clear_skies_book.txt:1
    technical/government/Env_Prot_Agen/section-by-section_summary.txt:0
    technical/government/Env_Prot_Agen/tech_adden.txt:0
    technical/government/Env_Prot_Agen/tech_sectiong.txt:0

Similarly, ```grep -c``` can be used the print the number of instances of a specific word for all the files in a directory. Here, we can track how many times "climate" is used in each .txt file within Env_Prot_Agen.

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -c "chameleon" technical/* 
    grep: technical/911report: Is a directory
    grep: technical/biomed: Is a directory
    grep: technical/government: Is a directory
    grep: technical/plos: Is a directory

While ```grep -c``` can't be used for directories by itself, it can be combined with ```grep -r``` to track the number of instances of a pattern for every file in every directory. Below is a snippet of this (the full output is too long to copy and paste).

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -r -c "help" *
    technical/911report/chapter-2.txt:12
    technical/911report/chapter-1.txt:6
    technical/911report/chapter-5.txt:18
    technical/911report/chapter-6.txt:16
    technical/911report/chapter-7.txt:28
    technical/911report/chapter-9.txt:12
    technical/911report/chapter-8.txt:5
    technical/911report/preface.txt:3
    technical/911report/chapter-12.txt:22
    technical/911report/chapter-10.txt:5
    technical/911report/chapter-11.txt:2

## Printing More

There are 3 ways to print more of the text that matches the patterns. 

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -C2 "forest for debt" */*/*/final.txt
    recently borne fruit, particularly recent agreements with Japan and
    Italy to collaborate on climate modeling efforts and with El
    Salvador in a "forest for debt" swap that will preserve tropical
    forests there that sequester carbon. The complex challenge of
    global climate change requires a global response that will draw on

```grep -C3``` prints 3 more lines, above and below, from where the specific word was found. 

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -A1 "emphysema" */*/rr73.txt  

    In pulmonary emphysema, various inflammatory mediators
    have been suggested to cause tissue destruction and loss of
    --
    the pathogenesis of emphysema [ 6, 7]. Evidence, including
    the marked expansion of macrophage numbers in smokers'
    --
    emphysema [ 16, 17]. These concepts are not exclusive, and
    it is possible that several proteolytic and inflammatory
    mechanisms contribute to the development of emphysema.
    In the linked study [ 5], extended co-cultures of
    --
    important role in the development of emphysema. In animals,
    instillation of NE can result in the development of
    pulmonary emphysema [ 18]. Individuals deficient in α-1
    protease inhibitor, moreover, have an increased
    susceptibility to the development of emphysema [ 19, 20,
    21]. The current study suggests the possibility that NE can
    -- 
    development of emphysema. Mice deficient in MMP-9, MMP-12,
    or NE are resistant to the development of emphysema or skin
    blisters [ 8, 16]. Mice overexpressing collagenase,
    however, develop emphysema [ 14]. The current study
    proposes a possible collaboration among proteases that is
    --
    in diseases such as emphysema.

```grep -A1``` prints 1 lines below where the word was found.  The last line, "in diseases such as emphysema", has "emphysema", so nothing can be printed for after it.

    (base) ragalinapalaka@Ragalinas-MacBook-Pro skill-demo1 % grep -B4 "dysplasia" */*/cc1476.txt
    (rhinorrhea, tachypnea, and wheezing and/or rales); and
    nasopharyngeal secretions positive for RSV as determined
    by enzyme immunoassay. Preterm infants and infants with
    underlying cardiopulmonary disease, bronchopulmonary
    dysplasia, previous history of wheezing, or those needing
    --
    in our study group was 3.9 ± 1.1 days. Five infants
    received oxygen supplementation and eight infants needed
    intravenous fluids for more than 1 day. All infants were
    positive for RSV and none were premature or had
    bronchopulmonary dysplasia.

```grep -B4``` prints the 4 lines before when the phrase was used. Overall, this can be useful for gaining more context, seeing what similar phrases are used alongside the search phrase, and finding the key portions of text interest you. It allows users to tailor the information they receive and control how much or little they receive with each search.

