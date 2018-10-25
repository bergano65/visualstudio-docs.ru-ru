---
title: 'Практическое: создание ассоциаций файлов для приложения ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fd1bd7965f0277ce1d3d900be6ee10db097eeb3f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909111"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения могут быть связан один или несколько расширений имен файлов, так что приложение будет запускаться автоматически при открытии файла этих типов. Добавление поддержки расширения имени файла для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения прост.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Создание ассоциаций файлов для приложения ClickOnce  
  
1. Создание [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения обычно или использовать имеющуюся [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
2. Откройте манифест приложения в текстовом редакторе или редакторе XML, например в блокноте.  
  
3. Найдите элемент `assembly` . Дополнительные сведения см. в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Как дочерний `assembly` элемента, добавьте `fileAssociation` элемент. `fileAssociation` Элемент имеет четыре атрибута:  
  
   - `extension`: Расширение имени файла, который вы хотите связать с приложением.  
  
   - `description`: Описание типа файла, который будет отображаться в оболочке Windows.  
  
   - `progid`: Строка, однозначно определяющая тип файла, чтобы пометить его в реестре.  
  
   - `defaultIcon`: Значок, используемый для этого типа файлов. Значок должен быть добавлен как файловый ресурс в манифесте приложения. Для получения дополнительной информации см. [Практическое руководство. Включение файла данных в приложение ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Пример `file` и `fileAssociation` элементов, см. в разделе [ \<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Если вы хотите связать с приложением более чем один тип файлов, добавьте дополнительные `fileAssociation` элементов. Обратите внимание, что `progid` атрибут должен быть уникальным для каждого.  
  
6. После завершения работы в манифесте приложения, повторно подпишите манифест. Это можно сделать из командной строки с помощью Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Дополнительные сведения см. в разделе [Mage.exe (средство редактирования и создания)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>См. также  
 [\<fileAssociation > элемент](../deployment/fileassociation-element-clickonce-application.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (средство создания и редактирования манифеста)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



