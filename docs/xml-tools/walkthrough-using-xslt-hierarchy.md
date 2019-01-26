---
title: Пошаговое руководство. Использование XSLT иерархии
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dcbb61e0a23d1a530d9c104337454b7a8ba66ca7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020767"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Пошаговое руководство. Использование XSLT иерархии

Средство XSLT иерархии yпрощает многие задачи разработки XML. Таблица стилей XSLT часто использует инструкции `includes` и `imports`. Компиляция начинается с основной таблицы стилей. Ошибка, возникшая в ходе компиляции таблицы стилей XSLT, может иметь причиной другой источник, отличный от основной таблицы стилей. Для устранения ошибки или изменения таблицы стилей может потребоваться доступ к включенным или импортированным таблицам стилей. Пошаговое выполнение таблицы стилей в отладчике может открывать включенные и импортированные таблицы стилей и в какой-то момент может потребовать добавления точки останова в одной или более включенной таблице стилей.

Другой сценарий, при котором может пригодиться средство XSLT иерархии, - добавление точек останова во встроенные правила шаблона. Правила шаблона - это специальные шаблоны, создаваемые для каждого режима таблицы стилей и вызываемые из `xsl:apply-templates`, если ни один другой шаблон не совпадает с узлом. Для выполнения отладки встроенных правил шаблона отладчик XSLT создает файл с правилами во временной папке и компилирует их вместе с основной таблицей стилей. Процесс нахождения таблиц стилей, включенных в основную таблицу стилей, или нахождения и открытия таблицы стилей со встроенными правилами шаблона может усложниться, если не зайти в код одного из `xsl:apply-template`.

Пример, приведенный в данном разделе, демонстрирует процесс отладки таблицы стилей, на которую имеются ссылки.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Для отладки в таблице стилей, на который указывает ссылка

1. Откройте XML-документ в редакторе Visual Studio. В этом примере используется следующий документ:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Добавьте следующий *xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  Добавьте следующий *xslinclude.xsl* файла:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  Добавьте точку останова в инструкцию `<xsl:include href="xslincludefile.xsl" />`.

5.  Приступите к отладке.

6.  Когда отладчик останавливается в инструкцию `<xsl:include href="xslincludefile.xsl" />`, нажмите клавишу **шаг с заходом** кнопки. Отладка может быть продолжена в таблице стилей, на который указывает ссылка. Иерархия видима, а конструктор отображает верный путь.

## <a name="see-also"></a>См. также

- [Пошаговое руководство: Профилировщик XSLT](../xml-tools/walkthrough-xslt-profiler.md)