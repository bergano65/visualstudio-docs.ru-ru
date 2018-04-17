---
title: Интеграция с редактором XML | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 864c00b26cd4b11e040d93318602ada92464463f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="integration-with-xml-editor"></a>Интеграция с редактором XML
Конструктор XML-схем объединен с редактором XML. Если вы измените XSD-файл в редакторе XML, изменения будут отражены в [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md). Если у вас есть [представление графика](../xml-tools/graph-view.md) или [представления модели содержимого](../xml-tools/content-model-view.md) открыт, изменения будут отражены и в них. Можно перемещаться между конструктором XML-схем и редактором XML, используя любой из следующих методов.  
  
-   В редакторе XML щелкните правой кнопкой мыши узел и выберите **Показать в обозревателе XML-схем**.  
  
-   В представлении графиков и обозревателе XML-схем, дважды щелкните узел, или щелкните правой кнопкой мыши узел и выберите **Просмотр кода**. В представлении модели содержимого щелкните узел правой кнопкой мыши и выберите **Просмотр кода**.  
  
На следующем снимке экрана показана схема XML, открытая в обозревателе XML-схем. Обозреватель XML-схем отображает набор схем в виде дерева. XML Editor отображает текстовый вид узла, который сейчас активен в обозревателе XML-схем.  
  
![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
В некоторых случаях рекомендуется просматривать код в редакторе XML и графическом конструкторе параллельно. Чтобы просмотреть оба файла в то же время, щелкните правой кнопкой мыши в редакторе XML и выберите **конструктор представлений**. В меню Visual Studio Windows выберите **новый горизонтальных (или вертикальных) группу вкладок**.  
  
![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## <a name="see-also"></a>См. также  
 [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)