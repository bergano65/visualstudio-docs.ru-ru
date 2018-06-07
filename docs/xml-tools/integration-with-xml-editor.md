---
title: Интеграции конструктора XML-схем с помощью редактора XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573327"
---
# <a name="integration-with-xml-editor"></a>Интеграция с редактором XML

Конструктор XML-схем объединен с редактором XML. Если вы измените XSD-файл в редакторе XML, изменения будут отражены в [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md). Если у вас есть [представление графика](../xml-tools/graph-view.md) или [представления модели содержимого](../xml-tools/content-model-view.md) открыт, изменения будут отражены и в них. Можно перемещаться между конструктором XML-схем и редактором XML, используя любой из следующих методов.

-   В редакторе XML щелкните правой кнопкой мыши узел и выберите **Показать в обозревателе XML-схем**.

-   В представлении графика и **обозреватель XML-схем**, или дважды щелкните узел правой кнопкой мыши и выберите **Просмотр кода**. В представлении модели содержимого щелкните узел правой кнопкой мыши и выберите **Просмотр кода**.

На следующем рисунке показан схему XML, открытых в **обозреватель XML-схем**. **Обозреватель XML-схем** отображает набор схем в виде дерева. XML Editor отображает текстовый вид узла, активных в настоящий момент **обозреватель XML-схем**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

В некоторых случаях рекомендуется просматривать код в редакторе XML и графическом конструкторе параллельно. Чтобы просмотреть оба файла в то же время, щелкните правой кнопкой мыши в редакторе XML и выберите **конструктор представлений**. В меню Visual Studio Windows выберите **новый горизонтальных (или вертикальных) группу вкладок**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)