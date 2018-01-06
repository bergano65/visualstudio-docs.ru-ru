---
title: "Как: Создание XML-схемы из XML-документа | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0541e89e72670905172129ffbb141ae8ae9e727f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Как создать XML-схему из XML-документа
Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.  
  
-   Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.  
  
-   Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.  
  
-   Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.  
  
Созданные схемы затем используются для обеспечения поддержки технологии IntelliSense в XML-документе.  
  
Дополнительные сведения о модуле выведения схемы см. в разделе [вывод XML-схемы](/dotnet/standard/data/xml/inferring-an-xml-schema).  
  
### <a name="to-create-an-xml-schema"></a>Создание XML-схемы  
  
1.  Загрузите экземпляр XML-документа в XML Editor.  
  
2.  Нажмите кнопку **Create Schema** кнопку **инструментов**.  
  
     Документ схемы XML будет создан и открыт для каждого пространства имен в экземпляре XML-документа. Каждая схема открывается, как и любой временный файл.  
  
     Схемы можно сохранять на диск, добавлять в проект или удалять.  
  
    > [!NOTE]
    >  **Create Schema** команда также доступна в контекстном меню редактора XML и **XML** меню.  
  
## <a name="see-also"></a>См. также  
 [XML-редактор](../xml-tools/xml-editor.md)