# mimic3
research for MIMIC-III dataset
---
### guide to install
+ go to data folder and do `wget --user YOURUSERNAME --ask-password -A csv.gz -m -p -E -k -K -np -nd https://physionet.org/works/MIMICIIIClinicalDatabase/files/` with YOURUSERNAME is the email you register for mimic3 dataset
+ install postgresql `sudo apt-get install postgresql libpq-dev`
+ install pgadmin4: download `wget https://ftp.postgresql.org/pub/pgadmin3/pgadmin4/v1.3/pip/pgadmin4-1.3-py2.py3-none-any.whl` and do `pip install pgadmin*` in your conda environment
+ make your computer account a superuser for postgres: `sudo su - postgres` then `psql postgres` then `CREATE USER youraccount;`, `ALTER USER youraccount superuser;`, and `CREATE DATABASE mimic3 OWNER youraccount`
+ fork the repo `git clone --recursive https://github.com/AM2-Labs/mimic3.git`
+ go the the subfolder `cd mimic3/mimic-code/buildmimic/postgres/`
+ create tables `psql mimic3 -f postgres_create_tables.sql -U youraccount`
+ import data into tables `psql mimic3 -f postgres_load_data_gz.sql -U youraccount -v mimic_data_dir='<path_to_data>'`
+ add indices to database `psql mimic3 -f postgres_add_indexes.sql -U your account`
+ run pgadmin4: go to your python source folder of pgadmin4 `cd PATH/lib/python3.5/site-packages/pgadmin4`, do `python pgAdmin4.py`, and go to the browser `http://127.0.0.1:5050`

### practice to query
+ go to https://mimic.physionet.org/tutorials/intro-to-mimic-iii/ and practice

### understand tables
+ go to https://mimic.physionet.org/mimictables/admissions/
+ more at https://mimic.physionet.org/mimicdata/metavision/
+ an example: https://www.youtube.com/watch?v=S4Iyp_wONGc

### papers
+ https://scholar.google.co.kr/scholar?um=1&ie=UTF-8&lr&cites=4115250243685522
+ base line 1: https://cs224d.stanford.edu/reports/priyanka.pdf
+ base line 2: http://cs224d.stanford.edu/reports/lukelefebure.pdf
+ base line 3: http://cs229.stanford.edu/proj2016/report/TanigawaPfohl-ComputationalPredictionOfClinicalOutcomeOfSepsisFromCriticalCareDatabase-report.pdf
