# Schema

[![alt return](https://raw.githubusercontent.com/fiesta-framework/Art/master/Resources/signs.png) Main Menu](https://github.com/fiesta-framework/Docs/tree/3.2/#index)

- [Introduction](#introduction)

## Introduction

Schema are like making historic for your database allowing you to see all changes you made to the database structure, and also make the database structure more clearly for a team work.

The Fiesta Schema provides tools to create and update database tables,and also execute or cancel operations made on the database.

## Generating Schema

| Function | Arguments                                                                                                         | Description                                                                                                                                                          |
|----------|-------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| inc()    | $column : colmun name                                                                                             | adding incrementing integer ID column                                                                                                                                |
| string() | $column : colmun name                         $length : data lenght [optional] $default: default value [optional] | adding string column, $column is colmun name, you can pass in second argument the column size by default its 255, also you can pass default value in third argument. |
| int()    | $column : colmun name  $length: data lenght [optional]                                                            | adding integer column, $column is colmun name, you can pass in second argument the column size by default its 11.                                                    |
