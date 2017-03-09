---
title: "Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "развертывание ClickOnce, сопоставления файлов"
  - "сопоставления файлов, приложения ClickOnce"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Создание ассоциаций файлов для приложения ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] могут быть связаны с одним или несколькими расширениями имен файлов, так что приложение будет запускаться автоматически при открытии пользователем файла такого типа.  Добавление поддержки расширения имени файла в приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не вызывает затруднений.  
  
### Чтобы создать ассоциации файлов для приложения ClickOnce  
  
1.  Создайте приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] обычным способом или используйте существующее приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Откройте манифест приложения с помощью текстового редактора или XML\-редактора, такого как Блокнот в Windows.  
  
3.  Найдите элемент `assembly`.  Дополнительные сведения см. в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Добавьте элемент `fileAssociation` как дочерний элемент `assembly`.  Элемент `fileAssociation` имеет четыре атрибута:  
  
    -   `extension`: расширение имени файла, которое требуется связать с приложением.  
  
    -   `description`: описание типа файла, которое появляется в оболочке Windows.  
  
    -   `progid`: строка, однозначно определяющая тип файла, для его пометки в реестре.  
  
    -   `defaultIcon`: значок, используемый для этого типа файлов.  Значок должен быть добавлен как файловый ресурс в манифест приложения.  Дополнительные сведения см. в разделе [Практическое руководство. Включение файла данных в приложение ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Пример элементов `file` и `fileAssociation` см. в разделе [Элемент \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Если требуется связать с приложением более одного типа файлов, добавьте дополнительные элементы `fileAssociation`.  Обратите внимание, что для каждого типа файлов атрибут `progid` должен быть другим.  
  
6.  После того как работа с манифестом приложения завершена, заново подпишите манифест.  Это можно сделать из командной строки с помощью Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Дополнительные сведения см. в разделе [Mage.exe \(средство создания и редактирования манифеста\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## См. также  
 [Элемент \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(средство создания и редактирования манифеста\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)