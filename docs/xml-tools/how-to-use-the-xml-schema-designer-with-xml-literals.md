---
title: "Как использовать конструктор XML-схем с XML-литералами | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Как использовать конструктор XML-схем с XML-литералами
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описывается процесс просмотра схемы, связанной с XML\-литералом в проекте Visual Basic.  
  
### Создание нового проекта консольного приложения Visual Basic  
  
1.  Запустите Visual Studio 2010.  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем **Проект**.Откроется диалоговое окно **Создать проект**.В диалоговом окне **Типы проектов** выберите **Другие языки**, а затем **Visual Basic**.В разделе **Шаблоны** выберите «Консольное приложение».Затем введите `XMLLiterals` в поле **Имя** и местоположение проекта в поле **Местоположение**.Нажмите кнопку **OК**.  
  
     Создан новый проект.Проект XMLLiterals содержит один исходный файл Visual Basic, Module1.vb.  
  
### Добавление существующего XSD\-файла в проект  
  
1.  Откройте новый текстовый файл в приложении «Блокнот». Скопируйте образец кода XML\-схемы из источника [Схема заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.  
  
2.  Сохраните файл в любом местоположении под именем PurchaseOrderSchema.xsd.  
  
3.  В обозревателе решений щелкните правой кнопкой мыши имя проекта, выберите команду **Добавить**, затем **Существующий элемент…**.Откроется диалоговое окно **Добавлениесуществующего элемента**.Найдите файл PurchaseOrderSchema.xsd, выберите его и нажмите **Добавить**.  
  
     Проект XMLLiterals теперь содержит два файла: Module1.vb и PurchaseOrderSchema.xsd.  
  
### Добавление кода Visual Basic с XML\-литералом на основе XSD\-файла, включенного в проект  
  
1.  Замените код в файле Module1.vb на следующий код:  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Щелкните правой кнопкой мыши любой XML\-узел в XML\-литерале или импорте пространства имен XML и выберите пункт **Показать в обозревателе схем**.  
  
     Обозреватель XML\-схем будет отображен рядом с файлом Visual Basic, имеющим XML\-литерал, связанный с набором XML\-схем.