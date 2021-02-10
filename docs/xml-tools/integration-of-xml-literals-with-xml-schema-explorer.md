---
title: Интеграция XML-литералов с обозревателем XML-схем
description: Узнайте, как использовать поддержку XML-литералов в обозревателе XML-схем в Visual Studio для интеграции XML-фрагментов непосредственно в код Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57a29998-c6e8-48ac-bdb0-5788e73f9164
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46020dc8423da617deb8f4f70c2a159b4a32014
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851547"
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
