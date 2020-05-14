---
title: Интеграция конструктора схем XML с редактором XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a9220d84e2fb1a15545d1a880b0084952da77f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592585"
---
# <a name="integration-with-xml-editor"></a>Интеграция с редактором XML

Конструктор схем XML интегрирован с редактором XML. Если изменить файл XSD в редакторе XML, это изменение будет отражено в [обозревателе схем XML](../xml-tools/xml-schema-explorer.md). Если открыто [представление графика](../xml-tools/graph-view.md) или [представление модели содержимого](../xml-tools/content-model-view.md), изменения будут отражены и в них. Можно перемещаться между конструктором схем XML и редактором XML, используя любой из следующих методов.

- В редакторе XML щелкните правой кнопкой мыши узел и выберите **Показать в обозревателе схем XML**.

- В представлении графиков и **обозревателе схем XML** щелкните правой кнопкой мыши или дважды щелкните узел и выберите **Просмотреть код**. В представлении модели содержимого щелкните узел правой кнопкой мыши и выберите **Просмотреть код**.

На следующем снимке экрана показана схема XML, открытая в **обозревателе схем XML**. **Обозреватель схем XML** отображает набор схем в виде дерева. Редактор XML отображает текстовое представление узла, который сейчас активен в **обозревателе схем XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

В некоторых случаях рекомендуется просматривать код в редакторе XML и графическом конструкторе параллельно. Чтобы просмотреть оба файла одновременно, щелкните правой кнопкой мыши в редакторе XML и выберите **Конструктор представлений**. В меню Visual Studio Windows выберите **Создать группу горизонтальных (или вертикальных) вкладок**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
