---
title: Интеграция конструктора XML-схем с редактором XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faad46c6ac2686de69fcb33f2fb482bdb0f4fe00
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525144"
---
# <a name="integration-with-xml-editor"></a>Интеграция с редактором XML

Конструктор XML-схем интегрирован с редактором XML. Если изменить XSD-файл в редакторе XML, изменения будут отражены в [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md). Если у вас есть [представление графика](../xml-tools/graph-view.md) или [представления модели содержимого](../xml-tools/content-model-view.md) open, изменения будут также отражены существует. Можно перемещаться между конструктор XML-схем и редактором XML следующим образом:

-   В редакторе XML, щелкните правой кнопкой мыши узел и выберите **Показать в обозревателе XML-схем**.

-   В представлении графика и **обозреватель XML-схем**, дважды щелкните узел, или щелкните правой кнопкой мыши узел и выберите **Просмотр кода**. В представлении модели содержимого щелкните узел правой кнопкой мыши и выберите **Просмотр кода**.

На следующем рисунке показан схему XML, открывается в **обозреватель XML-схем**. **Обозреватель XML-схем** отображает набор схем в виде дерева. XML editor отображает текстовый вид узла, активных в данный момент **обозреватель XML-схем**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Иногда бывает полезно видеть, код в редакторе XML и графическом конструкторе параллельно. Чтобы просмотреть оба файла в то же время, щелкните правой кнопкой мыши в редакторе XML и выберите **конструктор представлений**. В меню Visual Studio Windows выберите **новый горизонтальных (или вертикальных) группу вкладок**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)