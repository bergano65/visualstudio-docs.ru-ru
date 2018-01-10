---
title: "Пошаговое руководство: Использование XSLT иерархии | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e36ebaec08d09cbf006f4c20e743b5c2a909169
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Пошаговое руководство. Использование XSLT иерархии

Средство XSLT иерархии yпрощает многие задачи разработки XML. Таблица стилей XSLT часто использует инструкции `includes` и `imports`. Компиляция начинается с основной таблицы стилей. Ошибка, возникшая в ходе компиляции таблицы стилей XSLT, может иметь причиной другой источник, отличный от основной таблицы стилей. Для устранения ошибки или изменения таблицы стилей может потребоваться доступ к включенным или импортированным таблицам стилей. Пошаговое выполнение таблицы стилей в отладчике может открывать включенные и импортированные таблицы стилей и в какой-то момент может потребовать добавления точки останова в одной или более включенной таблице стилей.

Другой сценарий, при котором может пригодиться средство XSLT иерархии, - добавление точек останова во встроенные правила шаблона. Правила шаблона - это специальные шаблоны, создаваемые для каждого режима таблицы стилей и вызываемые из `xsl:apply-templates`, если ни один другой шаблон не совпадает с узлом. Для выполнения отладки встроенных правил шаблона отладчик XSLT создает файл с правилами во временной папке и компилирует их вместе с основной таблицей стилей. Процесс нахождения таблиц стилей, включенных в основную таблицу стилей, или нахождения и открытия таблицы стилей со встроенными правилами шаблона может усложниться, если не зайти в код одного из `xsl:apply-template`.

Пример, приведенный в данном разделе, демонстрирует процесс отладки таблицы стилей, на которую имеются ссылки.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Для отладки в таблицы стилей со ссылками

1. Откройте XML-документ в редакторе Visual Studio. В этом примере используется следующий документ `collection.xml`.  
  
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

1. Добавьте следующий метод `xslincludefile.xsl`:

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
  
3.  Добавьте следующий файл `xslinclude.xsl`:  
  
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
  
4.  Добавьте точку останова на этой инструкции `<xsl:include href="xslincludefile.xsl" />`.
  
5.  Приступите к отладке.  
  
6.  Когда отладчик останавливается на инструкции по `<xsl:include href="xslincludefile.xsl" />`, нажмите клавишу **шаг с заходом** кнопки. Заметьте, что отладка может быть продолжена в таблице стилей, на которую имеется ссылка. Иерархия видима, а конструктор отображает верный путь.  
  
## <a name="see-also"></a>См. также

[Пошаговое руководство. Профилировщик XSLT](../xml-tools/walkthrough-xslt-profiler.md)