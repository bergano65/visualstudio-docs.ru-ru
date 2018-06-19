---
title: 'Как: создание ассоциаций файлов для приложения ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf60327e622f8eb32757d29051e3dce94661722d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557766"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения могут быть связан один или несколько расширений имен файлов, так что приложение будет запускаться автоматически при открытии файла такого типа. Добавление поддержки расширения имени файла для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения несложно.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Создание сопоставлений файлов для приложения ClickOnce  
  
1.  Создание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение нормально, или использовать существующую [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
2.  Откройте манифест приложения с текстом или редакторе XML, например «Блокнот».  
  
3.  Найдите элемент `assembly`. Дополнительные сведения см. в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Как дочерний `assembly` элемента, добавьте `fileAssociation` элемента. `fileAssociation` Элемент имеет четыре атрибута:  
  
    -   `extension`: Расширение имени файла, который требуется связать с приложением.  
  
    -   `description`: Описание типа файла, которое будет отображаться в оболочке Windows.  
  
    -   `progid`: Строка, однозначно определяющая тип файла, чтобы пометить его в реестре.  
  
    -   `defaultIcon`: Значок, используемый для этого типа файлов. Значок должен быть добавлен как файловый ресурс в манифесте приложения. Для получения дополнительной информации см. [Практическое руководство. Включение файла данных в приложение ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Пример `file` и `fileAssociation` см [ \<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Если вы хотите связать с приложением более чем один тип файлов, добавьте дополнительные `fileAssociation` элементов. Обратите внимание, что `progid` должны быть различными для каждого атрибута.  
  
6.  После завершения работы в манифесте приложения, повторно подпишите манифест. Это можно сделать из командной строки с помощью Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Дополнительные сведения см. в разделе [Mage.exe (средство создания и манифеста редактирования)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>См. также  
 [\<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)