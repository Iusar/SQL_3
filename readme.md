## ����� ���� ������ SQL 

![](https://github.com/Iusar/SQL_3/blob/main/21.08.2021_database_diagram_#2.png)

## ��� SQL ��� �������� ���� ������ ��� ������� 2

```sql
CREATE TABLE IF NOT EXISTS ����������� (
	id_artist SERIAL PRIMARY key,
	��� VARCHAR(50) NOT NULL unique,
	id_genre INTEGER NOT NULL unique
);
CREATE TABLE IF NOT EXISTS ������� (
	id_album SERIAL PRIMARY key,
	��������_������� VARCHAR(100)  NOT NULL, 
	���_������� VARCHAR(4) NOT NULL,
	id_artist INTEGER REFERENCES �����������(id_artist) NOT NULL
);
CREATE TABLE IF NOT EXISTS ����� (
	id_track SERIAL PRIMARY key,
	��������_����� VARCHAR(100)  NOT NULL,
	������������ VARCHAR(10) NOT NULL,
	id_album INTEGER REFERENCES �������(id_album) NOT NULL
);
CREATE TABLE IF NOT EXISTS ����� (
	id_genre SERIAL PRIMARY key,
	��������_����� VARCHAR(100)  NOT NULL UNIQUE
);
ALTER TABLE ����������� ADD CONSTRAINT id_genre FOREIGN KEY (id_genre) REFERENCES �����(id_genre);
```
## ������� SQL ��� ��������� ���� ������ ��� ������� 3

```sql

ALTER TABLE ����������� DROP COLUMN id_genre;

CREATE TABLE IF NOT EXISTS �����_����������� (
	id_genre INTEGER REFERENCES �����(id_genre) NOT null,
	id_artist INTEGER REFERENCES �����������(id_artist) NOT null
);	
CREATE TABLE IF NOT EXISTS �������_����������� (
	id_album INTEGER REFERENCES �������(id_album) NOT null,
	id_artist INTEGER REFERENCES �����������(id_artist) NOT null
);	
CREATE TABLE IF NOT EXISTS �������� (
	id_collection SERIAL PRIMARY key,
	��������_�������� VARCHAR(100)  NOT NULL, 
	���_������� VARCHAR(4) NOT NULL,
	id_track INTEGER REFERENCES �����(id_track) NOT NULL
);

```


