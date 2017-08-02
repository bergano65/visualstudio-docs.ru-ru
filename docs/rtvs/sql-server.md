---
title: "Интеграция SQL Server с инструментами R для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: ru-ru
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Работа с SQL Server и R

В инструментах R для Visual Studio (RTVS) используется поддержка SQL Server, реализованная в Visual Studio, призванная упростить анализ данных с помощью баз данных SQL, а именно создание и выполнение SQL-запросов, а также работу с хранимыми процедурами.

> [!Note]
> Для интеграции SQL с R необходимо установить SQL Server Data Tools.
> - Visual Studio 2017: запустите установщик Visual Studio и выберите рабочую нагрузку "Хранение и обработка данных", которая включает SQL Server Data Tools.
> - Visual Studio 2015: следуйте инструкциям в разделе [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

В следующем видео (3 мин, 3 с) представлен краткий обзор SQL Server и R.

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Создание и выполнение SQL-запросов

RTVS поддерживает добавление SQL-запросов в проекты R, позволяя итеративно разрабатывать SQL-запросы в отдельном контексте, пока не будут получены требуемые результаты.

Чтобы добавить файл SQL-запроса, щелкните правой кнопкой мыши проект в обозревателе решений выберите **Добавить > Новый элемент** и выберите в качестве типа файла **SQL-запрос**.

![Добавление элемента "SQL-запрос" в проект](~/docs/rtvs/media/sql-add-item.png)

Файл откроется в редакторе Transact-SQL в Visual Studio, в котором реализованы полная поддержка технологии IntelliSense для SQL и возможность выполнения запросов. Однако для работы этих функций необходимо подключиться к базе данных, используя кнопку "Подключить" на панели инструментов редактора или просто выполнить запрос (нажать клавиши CTRL + SHIFT + E, которые также можно использовать для выделенной области). В любом случае появляется диалоговое окно подключения.

![Диалоговое окно подключения SQL](~/docs/rtvs/media/sql-connection-dialog.png)

После установления соединения можно выполнять запросы и просматривать результаты.

![Окно с результатами выполнения SQL-запроса](~/docs/rtvs/media/sql-query-results.png)

Редактор Transact-SQL поддерживает множество других функций, таких как просмотр плана выполнения запроса, отладчик запросов. В редакторе Transact-SQL также доступны многие другие функции. Дополнительные сведения см. в разделе [Использование редактора Transact-SQL для редактирования и выполнения скриптов](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Работа с хранимыми процедурами SQL Server

[Службы SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 и более поздние версии) позволяют внедрять и выполнять код R из хранимых процедур T-SQL. Это означает, что код R можно выполнять на компьютере с SQL Server, работать с данными, возвращаемыми SQL-запросом, а также создавать наборы результатов SQL, которые можно далее обработать в SQL или возвратить клиенту.

RTVS упрощает громоздкий и подверженный ошибкам процесс объединения SQL с кодом R, используя вместо него одну инструкцию SQL, как описано в следующих разделах.

- [Добавление подключения к базе данных](#add-a-database-connection)
- [Написание и тестирование хранимой процедуры SQL](#write-and-test-a-sql-stored-procedure)
- [Публикация хранимой процедуры SQL](#publish-a-sql-stored-procedure)

В следующем видео (6 мин, 9 с) представлен обзор этих функций.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Добавление подключения к базе данных

1. Выберите **Инструменты R > Данные > Добавить подключение к базе данных**, чтобы отобразить диалоговое окно **Свойства подключения**, в котором укажите имя источника данных (в данном случае — SQL Server), имя сервера, режим проверки подлинности и имя базы данных. Можно нажать кнопку **Проверить подключение** для проверки введенных данных, прежде чем закрывать диалоговое окно.
 
    ![Диалоговое окно подключения SQL](~/docs/rtvs/media/sql-connection-string-dialog.png)

1. После указания допустимых настроек подключения и нажатия кнопки **ОК** Visual Studio создает строку подключения с именем `dbConnection` в новом файле `settings.R`. RTVS автоматически выполняет этот файл, чтобы это подключение можно было сразу использовать в скриптах R.

![Файл Settings.R для SQL](~/docs/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Написание и тестирование хранимой процедуры SQL

Чтобы добавить новую хранимую процедуру SQL, щелкните правой кнопкой мыши проект, выберите **Добавить > Новый элемент**, выберите в списке шаблонов пункт **Хранимая процедура SQL с R**, присвойте файлу имя (в этом примере "`StoredProcedure.R`") и нажмите кнопку **ОК**.
 
RTVS создает три файла для хранимой процедуры: файл `.R` для кода R, файл `.Query.sql` для кода SQL и файл `.Template.sql`, в котором объединены эти два кода. Последние два отображаются в обозревателе решений как дочерние элементы файла `.R`.

![Развернутое окно обозревателя решений с хранимой процедурой SQL с R](~/docs/rtvs/media/sql-solution-explorer-expanded.png)

Файл `StoredProcedure.R` (в данном примере), который используется для написания кода R. Содержимое по умолчанию выглядит следующим образом.

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Проще говоря, код получает кадр данных R, который называется `InputDataSet`, и возвращает свои результаты в `OutputDataSet`, а код шаблона просто копирует входные данные в вывод.

> [!Note]
> Для управления именами этих кадров данных используются параметры `@input_data_1_name` и `@output_data_1_name` в вызове системной хранимой процедуры `sp_execute_external_script`. Дополнительные сведения о проектировании этого соглашения о вызовах и некоторые примеры его использования см. в разделе [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Другой сгенерированный код в комментариях является небольшим сценарием теста, который использует [пакет RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) для передачи инструкции SQL в SQL Server, запускает его и получает результирующий набор в виде кадра данных R. Можно раскомментировать этот код теста для интерактивного создания собственного кода R на основе результирующего набора, полученного от SQL Server.

Файл `StoredProcedure.Query.sql` используется для записи и проверки SQL-запроса, который генерирует данные для `InputDataSet`. Поскольку это файл `.sql`, вам доступны все функции Transact-SQL редактора.

Оформив код SQL требуемым образом, его можно с легкостью интегрировать с кодом R в файле `StoredProcedure.R`, просто перетащив файл `.sql` в редактор, в котором открыт файл `.R`. На рисунке ниже файл `StoredProcedure.Query.sql` перемещен в место после запятой в переменной `sqlQuery(channel, )`.

![Считывание содержимого файла SQL в строковую переменную R](~/docs/rtvs/media/sql-reference-sql-file-from-r.png)

Как видно, при выполнении этого простого действия автоматически создается код R для открытия файла `.sql`, считывания его содержимого в строку и его передачи в пакет RODBC для отправки в SQL Sever.

Здесь теперь можно в интерактивном режиме написать код R, который управляет кадром данных `InputDataSet` требуемым образом. Помните, что можно просто выбрать код R в редакторе и отправить его в [интерактивное окно](interactive-repl.md) нажатием клавиш CTRL + ВВОД.

Наконец, в файле `StoredProcedure.Template.sql` находится шаблон для создания хранимой процедуры SQL.

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- Заполнитель `_RCODE_` заменяется содержимым файла `StoredProcedure.R`.
- Заполнитель `_INPUT_QUERY_` заменяется содержимым файла `StoredProcedure.Query.sql`.
- Необходимо описать схему результирующего набора, который возвращается из хранимой процедуры, изменив предложение `WITH RESULT SETS`. В частности, необходимо определить столбцы из кадра данных `OutputDataSet`, которые требуется вернуть вызывающему хранимую процедуру. 

Например, для следующего запроса:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Необходимо использовать следующее предложение `WITH RESULT SETS` для указания типов данных возвращаемых значений.

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Публикация хранимой процедуры SQL

1. Выберите команду **Инструменты R > Данные > Опубликовать с параметрами**.
1. В появившемся диалоговом окне выберите для параметра **Публикация в:** значение **База данных**, укажите целевой объект, нажмите **Опубликовать**, после чего RTVS создаст и опубликует хранимую процедуру.

    ![Диалоговое окно публикации хранимой процедуры](~/docs/rtvs/media/sql-publish-with-options.png)

1. Чтобы опубликовать все хранимые процедуры в проекте, можно воспользоваться командой **Инструменты R > Данные > Опубликовать хранимые процедуры**, которая также доступна в контекстном меню проекта в обозревателе решений.

> [!Tip]
> Если в Visual Studio открыт обозреватель объектов SQL Server, опубликованная хранимая процедура также отобразится в папке **Программирование > Хранимые процедуры** базы данных. Процедуру также можно выполнить в обозревателе объектов, щелкнув ее правой кнопкой мыши и выбрав **Выполнить процедуру** или путем ее интерактивного вызова в окне запроса `.sql`.

