---
title: "Советы и рекомендации по безопасности в пакетах VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770dff4b531bf4a7347cb648ca4c930b28b79bea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по безопасности в пакетах VSPackage
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] на компьютере, должна быть запущена в контексте с учетными данными администратора. Базовая единица безопасность и развертывание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приложение [пакетов VSPackage](../../extensibility/internals/vspackages.md). Пакет VSPackage должен быть зарегистрирован с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], что также требует учетные данные администратора.  
  
 Администраторы имеют полные разрешения для записи в реестре и файловой системе, а также для выполнения любого кода. Необходимо иметь следующие разрешения для разработки, развертывания или установки пакетов VSPackage.  
  
 Сразу после установки пакета VSPackage является полностью доверенным. Из-за такой высокий уровень разрешений, связанных с VSPackage можно случайно установить VSPackage, злоумышленников.  
  
 Пользователям следует убедиться, что они установку пакетов VSPackage только из надежных источников. Компании разработка пакетов VSPackage должен строго имени и подписывать их, для обеспечения пользователя, изменение данных запрещен. Разработка пакетов VSPackage компании следует изучить их внешних зависимостей, таких как веб-службы и удаленной установки, для оценки и исправления проблем с безопасностью.  
  
 Дополнительные сведения см. в разделе правила написания безопасного кода для платформы .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>См. также  
 [Безопасность надстроек](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Безопасность DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)