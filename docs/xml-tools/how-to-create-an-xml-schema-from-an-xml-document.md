---
title: Создание XML-схемы
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10ce1c6dc5bd24b391a8cde184a32684270662ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815452"
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
