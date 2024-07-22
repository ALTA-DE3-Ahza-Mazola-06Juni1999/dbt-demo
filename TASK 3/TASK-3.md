## TASK 3 

Langkah-langkah setup dbt:

 #### 1. buat venv
```
python3 -m venv .venv
```

#### 2. Masuk ke dalam venv
```
source .venv/bin/activate
```

#### 4. Jalankan docker 
```
docker compose up
```

![alt text](<docker compose up .png>)

#### 5. Install dbt-postgres
```
pip install dbt-postgres
```

![alt text](<install dbt-postgres.png>)

#### 6. Melihat packages DBT apa saja yang sudah terinstall
```
pip freeze| grep dbt
```

![alt text](image.png)

#### 7. Simpan list packages DBT ke dalam file requirements.txt
 ```
 pip freeze | grep dbt >> requirements.txt
 ```

![alt text](image-1.png)

#### 8. Setup DBT project
```
dbt init my_project
```

![alt text](image-2.png)

Secara default, DBT akan menbuat sebuah dbt profile di home directory `~/.dbt/profiles.yml`

untuk membuat dbt-profile direktori baru, kita bisa menjalankan:
```
mkdir dbt-profiles

touch dbt-profiles/profiles.yml

export DBT_PROFILES_DIR=$(pwd)/dbt-profiles
```
![alt text](image-3.png)

#### 9. Setup DBT project congfiguration

pastikan models di dbt_project.yml terlihat seperti ini:
```
models:
  my_project:
    # Config indicated by + and applies to all files under models/example/
    store:
      +schema: public
      +database: store
    store_analytics:
      +materialized: table
      +schema: analytics
      +database: store

``` 
![alt text](image-4.png)

#### 10. Membuat model baru
- buat direktori store_analytic di dalam direktori models `mkdir store_analytic`
`touch store_analytic/schema.yml`

![alt text](image-5.png)

- Kemudian definisikan `schema.yml`

![alt text](image-6.png)

- Kemudian definisikan tabel dengan menambah file `daily_sales.sql` di dalam direktori yang sama.

![alt text](image-7.png)

![alt text](image-9.png)

#### 11. Run dan test model
```
cd my_project
dbt run
dbt test
```





