---
title: 'Практическое: создать схему XML из XML-документа | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: df8240552ac78fa81baef9f48a0cc00afb25fd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572026"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Как создать XML-схему из XML-документа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: создать схему XML из XML-документа](https://docs.microsoft.com/visualstudio/xml-tools/how-to-create-an-xml-schema-from-an-xml-document).  
  
  
Редактор XML позволяет создать схему на языке XSD из XML-документа. Экземпляр XML-документа определяет способ создания схемы следующим образом.  
  
-   Если с XML-документом не связана схема или определение типа документа (DTD), данные в XML-документе используются для создания новой схемы XML.  
  
-   Если XML-документ содержит связанное определение DTD, то внешнее определение DTD и встроенное определение DTD преобразуются в соответствующую схему XML.  
  
-   Если XML-документ содержит встроенную схему XDR, схема XDR преобразуется в соответствующую схему XML.  
  
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



