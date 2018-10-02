---
title: 'Пошаговое руководство: Отладка таблицы стилей XSLT | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 969bccce307683252c695ebe1d337aa08b04d022
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557527"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Пошаговое руководство: отладка таблицы стилей XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаги в данном пошаговом руководстве демонстрируют, как использовать XSLT-отладчик. Шаги включают просмотр переменных, задание точек останова и пошаговое прохождение кода. Таблица стилей находит все книги, которые стоят меньше средней цены книги.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Чтобы подготовиться к выполнению данного пошагового руководства  
  
1.  Закройте все открытые решения.  
  
2.  Скопируйте два файла с образцами на локальный компьютер.  
  
## <a name="start-debugging"></a>Начало отладки  
  
#### <a name="to-start-debugging"></a>Начало отладки  
  
1.  Из **файл** последовательно выберите пункты **откройте**и нажмите кнопку **файл**.  
  
2.  Найдите файл belowAvg.xsl и нажмите кнопку **откройте**.  
  
     Таблица стиля откроется в XML-редакторе.  
  
3.  Нажмите кнопку обзора (**...** ) на **ввода** поле из окна свойств документа.  
  
4.  Найдите файл books.xml и нажмите кнопку **откройте**.  
  
     Таким образом задается файл исходного документа, используемого в XSLT-преобразовании.  
  
5.  Щелкните правой кнопкой мыши `xsl:if` открывающего тега, укажите **точки останова**и нажмите кнопку **вставить точку останова**.  
  
6.  Нажмите кнопку **Отладка XSL** кнопки на панели инструментов редактора XML.  
  
 Это запускает процесс отладки и открывает несколько новых окон, которые используются отладчиком.  
  
 Входной документ и таблица стиля отображаются в двух окнах. Отладчик использует эти окна, чтобы показывать текущее состояние выполнения. Отладчик располагается на элементе `xsl:if` таблицы стиля и на первом узле книги файла books.xml.  
  
 Окно локальных значений отображает все локальные переменные и их текущие значения. Сюда относятся переменные, определенные в таблице стиля, а также переменные, используемые отладчиком для отслеживания узлов, которые в настоящий момент находятся в контексте.  
  
 **Вывод XSL** окно отображает результат XSL-преобразования. Это окно существует наряду с **вывода Visual Studio** окна.  
  
## <a name="watch-window"></a>Окно “Контрольное значение”  
  
#### <a name="to-use-the-watch-window"></a>Использование окна просмотра значений  
  
1.  Из **Отладка** последовательно выберите пункты **Windows**, пункты **Watch**и нажмите кнопку **Контрольные значения 1**.  
  
     Отобразится окно «Просмотр 1».  
  
2.  Тип `$bookAverage` в **имя** поле и нажмите клавишу ВВОД.  
  
     В окне отобразится значение переменной `$bookAverage`.  
  
3.  Тип `self::node()` в **имя** поле и нажмите клавишу ВВОД.  
  
     `self::node()` является выражением XPath, которое вычисляется до текущего узла контекста. Значение `self::node()` выражения XPath является первым узлом книги. Оно меняется по мере прохождения преобразования.  
  
4.  Раскройте узел `self::node()`, а затем узел `price`.  
  
     Это позволяет увидеть значение цены книги, и его можно легко сравнить со значением `$bookAverage`. Так как цена книги ниже средней, условие `xsl:if` должно выполняться.  
  
## <a name="step-through-the-code"></a>Пошаговое прохождение кода   
 Отладчик позволяет выполнять код по одной строке.  
  
#### <a name="to-step-through-the-code"></a>Пошаговое прохождение кода  
  
1.  Чтобы продолжить выполнение, нажмите клавишу **F5**.  
  
     Так как первый узел книги удовлетворяет условию `xsl:if`, узел книги добавляется в окно вывода XSL. Отладчик продолжает выполнение, пока не будет вновь достигнут элемент `xsl:if` в таблице стилей. Теперь отладчик располагается на втором узле книги в файле books.xml.  
  
     В окне «Просмотр 1» значение `self::node()` изменяется на второй узел книги. Проверив значение элемента цены, можно определить, что цена выше средней; таким образом, условие `xsl:if` не выполняется.  
  
2.  Чтобы продолжить выполнение, нажмите клавишу **F5**.  
  
     Так как второй узел книги не удовлетворяет условию `xsl:if`, узел книги не добавляется в окно вывода XSL. Отладчик продолжает выполнение, пока не будет вновь достигнут элемент `xsl:if` в таблице стилей. Теперь отладчик располагается на третьем узле `book` в файле books.xml.  
  
     В окне «Просмотр 1» значение `self::node()` изменяется на третий узел книги. Проверив значение элемента `price`, можно определить, что цена ниже средней; таким образом, условие `xsl:if` выполняется.  
  
3.  Чтобы продолжить выполнение, нажмите клавишу **F5**.  
  
     Так как условие `xsl:if` выполняется, третья книга добавляется в окно «Вывод XSL». Все книги в XML-документе обработаны, отладчик прекращает выполнение.  
  
## <a name="sample-files"></a>Файлы образца  
 В этом пошаговом руководстве используются следующие два файла.  
  
### <a name="belowavgxsl"></a>belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="booksxml"></a>books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)

