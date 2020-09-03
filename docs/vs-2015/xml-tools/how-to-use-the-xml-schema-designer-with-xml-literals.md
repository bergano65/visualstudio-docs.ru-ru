---
title: Как использовать конструктор XML-схем с XML-литералами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656297"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Практическое руководство. Использование конструктора схем XML с XML-литералами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описывается процесс просмотра схемы, связанной с XML-литералом в проекте Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Создание нового проекта приложения командной строки Visual Basic

1. Запустите Visual Studio 2010.

2. В меню **Файл** выберите команду **Создать**, а затем пункт **Проект**. Откроется диалоговое окно **Новый проект** . Для **типов проектов**выберите **другие языки,** а затем выберите **Visual Basic**. В качестве **шаблона**выберите Консольное приложение. Затем `XMLLiterals` в поле **Расположение** введите **имя** и расположение проекта. Нажмите кнопку **ОК**.

     Создан новый проект. Проект XMLLiterals содержит один исходный файл Visual Basic, Module1.vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Добавление существующего XSD-файла в проект

1. Откройте новый текстовый файл в блокноте. Скопируйте образец кода XML-схемы из [схемы заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.

2. Сохраните файл в любом местоположении под именем PurchaseOrderSchema.xsd.

3. В обозреватель решений щелкните правой кнопкой мыши имя проекта, выберите **Добавить**, а затем выберите **существующий элемент...**. Откроется диалоговое окно **Добавление существующего элемента**. Найдите файл PurchaseOrderSchema.xsd, выберите его и нажмите кнопку **Добавить**.

     Проект XMLLiterals теперь содержит два файла: Module1.vb и PurchaseOrderSchema.xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Добавление кода Visual Basic с XML-литералом на основе XSD-файла, включенного в проект

1. Замените код в файле Module1.vb на следующий код:

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

2. Щелкните правой кнопкой мыши любой XML-узел в XML-литерале или импорте пространства имен XML и выберите пункт **Show in Schema Explorer** (Показать в обозревателе схем).

     Обозреватель XML-схем будет отображен рядом с файлом Visual Basic, имеющим XML-литерал, связанный с набором XML-схем.
