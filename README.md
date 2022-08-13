# Memisahkan data sensitif dengan view table

Table view adalah tabel virtual yang dibuat oleh query yang bertujuan untuk memudahkan penyajian data. Pada kasus kali ini akan dibuat tabel yang berisi data sensitif atau pribadi dengan menggunakan view table untuk memudahkan jika ingin melihat data pribadi dari pekerja.

Projek kali ini akan menggunakan 5 scema atau tabel yaitu tabel employees, Job_History, Jobs, Departments dan locations

![TABELTABEL](https://github.com/ajrielrahayu/SQL-Memisahkan-data-sensitif-dengan-view-table/blob/main/DOCS/TABELTABEL.png)

view table yang akan dibuat diberi nama tabel "Sensitif" yang isinya nama, id, tanggal kelahiran, gender dan penghasilan.

Berikut sintaknya :

```
CREATE VIEW SENSITIF AS
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, SALARY
FROM EMPLOYEES;
```

kemudian kita bisa melihat tabelnya dengan :

```
SELECT * FROM SENSITIF
```

output yang dihasilkan adalah :

![TABELTABEL](https://github.com/ajrielrahayu/SQL-Memisahkan-data-sensitif-dengan-view-table/blob/main/DOCS/HASIL1.png)

Jika kita ingin memperbaharui atau mengubah tampilan tabel bisa menggunakan replace.
Berikut sintaknya :

```
CREATE OR REPLACE VIEW SENSITIF  AS
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, JOB_TITLE, MIN_SALARY, MAX_SALARY
FROM EMPLOYEES, JOBS
WHERE EMPLOYEES.JOB_ID = JOBS.JOB_IDENT;
```

Kemudian kita panggil tabelnya :

```
SELECT * FROM SENSITIF
```

Berikut outputnya :

![TABELTABEL](https://github.com/ajrielrahayu/SQL-Memisahkan-data-sensitif-dengan-view-table/blob/main/DOCS/HASIL2.png)


dan jika ingin menghapus tabel sensitif bisa dilakukan dengan :

```
DROP VIEW SENSITIF;
```
