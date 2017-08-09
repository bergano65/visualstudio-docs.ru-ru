---
title: "Использование разметки R Markdown с инструментами R для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: ru-ru
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>Создание документов R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) представляет собой формат документов, позволяющие превратить анализ в R в высококачественные документы, отчеты, презентации и панели мониторинга.

В Инструментах R для Visual Studio (RTVS) имеются шаблон элемента R Markdown, поддержка редактора (включая IntelliSense для кода R в самом редакторе) и возможности по созданию файлов.

Использование разметки R Markdown

1. Закройте Visual Studio.
1. Установите `pandoc` с сайта [pandoc.org](http://pandoc.org/installing.html) (только один раз).
1. Перезапустите Visual Studio, после чего программное обеспечение будет обновлено с учетом установки pandoc.
1. Установите пакеты `knitr` и `rmarkdown`, что можно сделать в [интерактивном окне](interactive-repl.md).

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Создайте новый файл R Markdown, воспользовавшись командой **Файл > Создать** и выбрав в списке пункт **R Markdown** или щелкнув правой кнопкой мыши проект в обозревателе решений и выбрав **Добавить разметку R Markdown** (или **Добавить > Новый элемент** и выбрав в списке **R Markdown**).

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

1. Можно в любое время в процессе редактирования щелкнуть правой кнопкой мыши в окне редактора и выбрать пункт **Предварительный просмотр**, в котором имеются параметры для просмотра в форматах HTML, PDF и Microsoft Word. В этом окне предварительного просмотра файл можно сохранить в требуемом формате.

