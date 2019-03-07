---
title: Создание схемы XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526133"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Практическое руководство. Создание схемы XML из XML-документа

Редактор XML позволяет создать схему языка определения схемы XML из XML-документа. XML-файл определяет способ создания схемы следующим образом:

- Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.

- Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.

- Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.

Созданные схемы затем используются для предоставления функции IntelliSense для XML-файле.

Дополнительные сведения о модуле выведения схемы см. в разделе [вывести схему XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML

1. Откройте XML-файл в Visual Studio.

2. В строке меню выберите **XML** > **Create Schema**.

   Документ схемы XML создается и открывается для каждого пространства имен в XML-файле. Каждая схема открывается, как и любой временный файл. Схемы можно сохранять на диск, добавлять в проект или удалять.

## <a name="see-also"></a>См. также

- [Редактор XML](../xml-tools/xml-editor.md)