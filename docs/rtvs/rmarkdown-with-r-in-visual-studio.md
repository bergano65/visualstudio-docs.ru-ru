---
title: Разметка R
description: Практическое руководство по созданию документов R Markdown в Visual Studio и составлению качественных отчетов, презентаций и панелей мониторинга.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: bc8ffe0f6d3cdc0cd572c39dedb5f059e63525cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="creating-r-markdown-documents"></a>Создание документов R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) представляет собой формат документов, позволяющие превратить анализ в R в высококачественные документы, отчеты, презентации и панели мониторинга.

Инструменты R для Visual Studio (RTVS) включают шаблон элемента R Markdown, поддержку редактора (включая IntelliSense для кода R в самом редакторе), а также функции создания файлов и динамического просмотра.

## <a name="using-r-markdown"></a>Использование R Markdown

1. Закройте Visual Studio.
1. Установите `pandoc` с сайта [pandoc.org](http://pandoc.org/installing.html) (только один раз).
1. Перезапустите Visual Studio, после чего программное обеспечение будет обновлено с учетом установки pandoc.
1. Установите пакеты `knitr` и `rmarkdown`, что можно сделать в [интерактивном окне](interactive-repl-for-r-in-visual-studio.md).

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Создайте файл R Markdown, последовательно выбрав команды меню **"Файл" > "Создать" > "Файл"**, а затем выбрав **"R" > "R Markdown"** в списке. Находясь в контексте проекта, щелкните проект правой кнопкой мыши в обозревателе решений и выберите **Добавить разметку R Markdown** (или **"Добавить" > "Новый элемент…"**, а затем выберите **R Markdown** в списке).

1. Содержимое по умолчанию в новом файле выглядит следующим образом.

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Предварительные версии

Visual Studio 2017 версии 15.5 и более поздних версий по умолчанию поддерживает для R Markdown функцию динамического просмотра. Чтобы включить автоматическую синхронизацию между редактором и предварительным просмотром, последовательно выберите **"Инструменты R" > "Markdown" > "Автоматическая синхронизация"** (CTRL+SHIFT+Y). Если вы не используете автоматическую синхронизацию, вы можете обновить содержимое предварительного просмотра, последовательно выбрав **"Инструменты R" > "Markdown" > "Перезагрузить предпросмотр R Markdown"**.

Вы также можете использовать предварительный просмотр файла в формате HTML, PDF и Microsoft Word. Для этого щелкните правой кнопкой мыши в редакторе и выберите одну из команд **предварительного просмотра**. Те же команды также доступны в меню **"Инструменты R" > "Markdown"**. (В более ранних версиях Visual Studio эти команды находились в меню **"Инструменты R" > "Опубликовать"**.)

![Динамический просмотр R Markdown и другие команды меню для предварительного просмотра](media/rmarkdown-live-preview.png)
