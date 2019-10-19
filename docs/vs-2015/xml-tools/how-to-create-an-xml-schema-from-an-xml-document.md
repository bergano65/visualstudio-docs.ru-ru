---
title: Как создать XML-схему из XML-документа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670931"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Как создать XML-схему из XML-документа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.

- Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.

- Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.

- Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.

  Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-документе.

  Дополнительные сведения о подсистеме вывода схемы см. в разделе [выведение схемы XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Создание XML-схемы

1. Загрузите экземпляр XML-документа в XML Editor.

2. Нажмите кнопку **CREATE SCHEMA (создать схему** ) на **панели инструментов**.

     Документ схемы XML будет создан и открыт для каждого пространства имен в экземпляре XML-документа. Каждая схема открывается, как и любой временный файл.

     Схемы можно сохранять на диск, добавлять в проект или удалять.

    > [!NOTE]
    > Команда **создать схему** также доступна в контекстном меню редактора XML и в меню **XML** .

## <a name="see-also"></a>См. также раздел
 [XML-редактор](../xml-tools/xml-editor.md)
