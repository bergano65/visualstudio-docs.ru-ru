---
title: Как создать XML-схему из XML-документа
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f33fc5b48b9fd6b1cc08570e62e73f05fd19e70
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548307"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Как: Создание XML-схемы из XML-документа

Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.

-   Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.

-   Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.

-   Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.

Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-документе.

Дополнительные сведения о модуле выведения схемы см. в разделе [вывод XML-схемы](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Порядок создания схемы XML

1.  Загрузите экземпляр XML-документа в XML Editor.

2.  Нажмите кнопку **Create Schema** кнопку **инструментов**.

     Документ схемы XML будет создан и открыт для каждого пространства имен в экземпляре XML-документа. Каждая схема открывается, как и любой временный файл.

     Схемы можно сохранять на диск, добавлять в проект или удалять.

    > [!NOTE]
    >  **Create Schema** команда также доступна в контекстном меню редактора XML и **XML** меню.

## <a name="see-also"></a>См. также

- [XML-редактор](../xml-tools/xml-editor.md)