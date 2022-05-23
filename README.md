# geo-app

## docker my-sql

    docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=password -d mysql

## geo spatial

### create table

    CREATE TABLE geom (name VARCHAR(191) NOT NULL, g GEOMETRY NOT NULL SRID 4326, SPATIAL INDEX(g));

### inset

    INSERT INTO geom VALUES ('Tokyo Station', ST_GeomFromText('POINT(35.680543724857934 139.76891501503698)', 4326));
    INSERT INTO geom VALUES ('South Tower', ST_GeomFromText('POINT(35.67867806522003 139.76737372342532)', 4326));
    INSERT INTO geom VALUES ('Tokyo International Forum', ST_GeomFromText('POINT(35.67673944955255 139.76375066005698)', 4326));

### select

    SELECT name, ST_AsText(g) FROM geom LIMIT 20;
    SELECT name,ST_AsText(g) g, ST_Distance_Sphere(g, ST_GeomFromText('POINT(35.680543724857934 139.76891501503698)', 4326)) d FROM geom where ST_Distance_Sphere(g, ST_GeomFromText('POINT(35.680543724857934 139.76891501503698)', 4326)) < 300 order by d;
