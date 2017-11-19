---
title: "Как: создание ассоциаций файлов для приложения ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 491de73e97bf44ea54d5ccdfb604924ff26c9530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]приложения могут быть связан один или несколько расширений имен файлов, так что приложение будет запускаться автоматически при открытии файла такого типа. Добавление поддержки расширения имени файла для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения несложно.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Создание сопоставлений файлов для приложения ClickOnce  
  
1.  Создание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение нормально, или использовать существующую [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
2.  Откройте манифест приложения с текстом или редакторе XML, например «Блокнот».  
  
3.  Найдите элемент `assembly`. Дополнительные сведения см. в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Как дочерний `assembly` элемента, добавьте `fileAssociation` элемента. `fileAssociation` Элемент имеет четыре атрибута:  
  
    -   `extension`: Расширение имени файла, который требуется связать с приложением.  
  
    -   `description`: Описание типа файла, которое будет отображаться в оболочке Windows.  
  
    -   `progid`: Строка, однозначно определяющая тип файла, чтобы пометить его в реестре.  
  
    -   `defaultIcon`: Значок, используемый для этого типа файлов. Значок должен быть добавлен как файловый ресурс в манифесте приложения. Для получения дополнительной информации см. [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Пример `file` и `fileAssociation` см [ \<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Если вы хотите связать с приложением более чем один тип файлов, добавьте дополнительные `fileAssociation` элементов. Обратите внимание, что `progid` должны быть различными для каждого атрибута.  
  
6.  После завершения работы в манифесте приложения, повторно подпишите манифест. Это можно сделать из командной строки с помощью Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Дополнительные сведения см. в разделе [Mage.exe (средство создания и манифеста редактирования)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>См. также  
 [\<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)