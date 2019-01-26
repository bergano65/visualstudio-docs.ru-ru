---
title: Как выполнить создать схему XML из XML-документа
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32072a25a57988c0cf1273518e5c0a5d4745fe20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033808"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Как выполнить Создание схемы XML из XML-документа

Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.

-   Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.

-   Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.

-   Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.

Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-документе.

Дополнительные сведения о модуле выведения схемы см. в разделе [выведение схемы XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML

1.  Загрузите экземпляр XML-документа в XML Editor.

2.  Нажмите кнопку **Create Schema** кнопки **инструментов**.

     Документ схемы XML будет создан и открыт для каждого пространства имен в экземпляре XML-документа. Каждая схема открывается, как и любой временный файл.

     Схемы можно сохранять на диск, добавлять в проект или удалять.

    > [!NOTE]
    >  **Create Schema** команда также доступна из контекстного меню редактора XML и **XML** меню.

## <a name="see-also"></a>См. также

- [XML-редактор](../xml-tools/xml-editor.md)