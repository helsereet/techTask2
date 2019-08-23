create database techtest;

use techtest;

create table PRODUCT
(
	[Id] INT PRIMARY KEY,
	[Name] NVARCHAR(MAX),
);

create table CATEGORY
(
	[Id] INT PRIMARY KEY,
	[Name] NVARCHAR(MAX)
);

create table PRODUCT_CATEGORY
(
	[ProductId] INT NOT NULL,
	[CategoryId] INT NOT NULL,
	foreign key ([ProductId]) references PRODUCT(Id),
	foreign key ([CategoryId]) references CATEGORY(Id),
	unique (ProductId, CategoryId)
);


SELECT
	P.Name, C.Name
FROM
	PRODUCT P
LEFT JOIN PRODUCT_CATEGORY PC on p.Id = PC.ProductId
LEFT JOIN CATEGORY C on PC.CategoryId = C.Id