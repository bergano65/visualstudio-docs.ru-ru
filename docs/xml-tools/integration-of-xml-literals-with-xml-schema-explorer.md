---
title: Интеграция XML-литералов с обозревателем XML-схем
description: Узнайте, как использовать поддержку XML-литералов в обозревателе XML-схем в Visual Studio для интеграции XML-фрагментов непосредственно в код Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57a29998-c6e8-48ac-bdb0-5788e73f9164
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 059263f06421fee3c90f2471df4c8b2c7bf8fc86
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398505"
---
# <a name="integration-of-xml-literals-with-xml-schema-explorer"></a>Интеграция XML-литералов с обозревателем XML-схем

Visual Basic поддерживает XML-литералы, что означает возможность включать XML-фрагменты непосредственно в код Visual Basic. Дополнительные сведения содержатся в разделе [Общие сведения об XML-литералах](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-overview).

## <a name="how-to"></a>Практическое руководство

Если XSD-файл в проекте Visual Basic содержит XML-литерал, то набор XML-схем можно просматривать в **обозревателе XML-схем**. Для просмотра набора схем, связанного с XML-литералом, щелкните правой кнопкой мыши узел XML в XML-литерале или импорте пространства имен XML, и выберите команду **Показать в обозревателе схем**.

![Снимок экрана: окно проекта Visual Basic с контекстным меню для узла XML с выделенной командой "Показать в обозревателе схем".](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer1.gif)

Это действие откроет **обозреватель XML-схем** параллельно файлу Visual Basic.

![Снимок экрана: окно проекта Visual Basic с открытыми обозревателем XML-схем и обозревателем решений в правой панели.](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer2.gif)

## <a name="see-also"></a>См. также

- [Практическое руководство. Использование конструктора схем XML с литералами XML](../xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals.md)
