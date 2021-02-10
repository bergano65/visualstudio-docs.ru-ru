---
title: Создание XML-схемы
description: Узнайте, как использовать редактор XML в Visual Studio для создания схемы на языке XSD из XML-документа.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970287"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Практическое руководство. Создание схемы XML из XML-документа

Редактор XML позволяет создать схему на языке XSD на основе XML-документа. XML-файл определяет способ создания схемы следующим образом:

- Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.

- Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.

- Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.

Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-файле.

Дополнительные сведения о модуле вывода схемы см. в статье [Выведение XML-схемы](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML

1. Откройте XML-файл в Visual Studio.

2. В строке меню выберите **XML** > **Создать схему**.

   Документ XML-схемы будет создан и открыт для каждого пространства имен в XML-файле. Каждая схема открывается, как и любой временный файл. Схемы можно сохранять на диск, добавлять в проект или удалять.

## <a name="see-also"></a>См. также

- [Редактор XML](../xml-tools/xml-editor.md)
