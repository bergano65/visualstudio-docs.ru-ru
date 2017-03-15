---
title: "Советы и рекомендации по обеспечению безопасности VSPackages | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по безопасности в пакеты VSPackage
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] на компьютере, необходимо использовать в контексте с учетными данными администратора. Базовая единица безопасность и развертывание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приложение [VSPackages](../../extensibility/internals/vspackages.md). VSPackage должны быть зарегистрированы с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], который также необходимы учетные данные администратора.  
  
 Администраторы имеют полные права на запись в реестре и файловой системе и для выполнения любого кода. Необходимо иметь следующие разрешения для разработки, развертывания или установить VSPackage.  
  
 Как только она установлена, VSPackage является полностью доверенным. Из-за такой высокий уровень разрешений, связанных с VSPackage можно случайно установить VSPackage, злоумышленников.  
  
 Пользователям следует убедиться в установке пакетов VSPackages только из надежных источников. Компаний, разрабатывающих VSPackages должно строго имени и их подписания, быть уверены, искажение запрещено. Компаний, разрабатывающих VSPackages следует проверить их внешние зависимости, такие как веб-службы и удаленной установки для оценки и устранения всех проблем безопасности.  
  
 Дополнительные сведения см. в разделе правила написания безопасного кода для платформы .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>См. также  
 [Безопасность надстроек](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX безопасности](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
