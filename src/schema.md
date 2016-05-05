# Schema

[![alt return](https://raw.githubusercontent.com/fiesta-framework/Art/master/Resources/signs.png) Main Menu](https://github.com/fiesta-framework/Docs/tree/3.2/#index)

- [Introduction](#introduction)

## Introduction

Schema are like making historic for your database allowing you to see all changes you made to the database structure, and also make the database structure more clearly for a team work.

The Fiesta Schema provides tools to create and update database tables,and also execute or cancel operations made on the database.

## Generating Schema

| Function                                                | Description                                                                                                                                                          |
|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| $table->inc($column)                                    | adding incrementing integer ID column                                                                                                                                |
| $table->string($column,$length = 255, $default = null ) | adding string column, $column is colmun name, you can pass in second argument the column size by default its 255, also you can pass default value in third argument. |
| $table->int($nom,$length=11)                            | adding integer column, $column is colmun name, you can pass in second argument the column size by default its 11.                                                    |
    
