---
title: Практическое руководство. Создание схемы XML из XML-документа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e601d03901484ed6e759fb336b1effa5b37841
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990176"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Практическое руководство. создать схему XML из XML-документа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.  
  
- Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.  
  
- Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.  
  
- Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.  
  
  Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-документе.  
  
  Дополнительные сведения о модуле выведения схемы см. в разделе [выведение схемы XML](http://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Создание XML-схемы  
  
1.  Загрузите экземпляр XML-документа в XML Editor.  
  
2.  Нажмите кнопку **Create Schema** кнопки **инструментов**.  
  
     Документ схемы XML будет создан и открыт для каждого пространства имен в экземпляре XML-документа. Каждая схема открывается, как и любой временный файл.  
  
     Схемы можно сохранять на диск, добавлять в проект или удалять.  
  
    > [!NOTE]
    >  **Create Schema** команда также доступна из контекстного меню редактора XML и **XML** меню.  
  
## <a name="see-also"></a>См. также  
 [XML-редактор](../xml-tools/xml-editor.md)
