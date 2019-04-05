---
title: Рекомендации по безопасности в пакетах VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1db578f62e6fe42ba3d74df5870ca727bd884aaf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990062"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по обеспечению безопасности при использовании пакетов VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы установить [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] на компьютере, необходимо использовать в контексте от имени администратора. Базовая единица безопасность и развертывание [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] приложение [пакетов VSPackage](../../extensibility/internals/vspackages.md). Необходимо зарегистрировать VSPackage с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], который также требуются административные учетные данные.  
  
 Администраторы имеют полные права доступа для записи в реестре и файловой системе, а также для выполнения любого кода. Необходимо иметь следующие разрешения для разработки, развертывания или установки пакетов VSPackage.  
  
 Как только установки VSPackage является полностью доверенным. Из-за высокий уровень разрешений, связанных с VSPackage существует возможность случайно установить пакет VSPackage, который злоумышленников.  
  
 Пользователям следует убедиться, что они установку пакетов VSPackage только из доверенных источников. Компании разработка пакетов VSPackage должен строго имени и подпишите их, для обеспечения предсказуемой, незаконное изменение запрещено. Разработка пакетов VSPackage компаниям следует проверить их внешние зависимости, такие как веб-службы и удаленной установки, чтобы оценить и устранить все проблемы безопасности.  
  
 Дополнительные сведения см. в разделе правил написания безопасного кода для .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>См. также  
 [Безопасность надстроек](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Безопасность DDEX](http://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
