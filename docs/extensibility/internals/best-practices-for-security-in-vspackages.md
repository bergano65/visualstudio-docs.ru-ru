---
title: Рекомендации по безопасности в пакетах VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5b3b86736a5425640c1a87df6a3e2c6e6cec0c5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513352"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по обеспечению безопасности в пакетах VSPackage
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] на компьютере, необходимо использовать в контексте от имени администратора. Базовая единица безопасность и развертывание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приложение [VSPackage](../../extensibility/internals/vspackages.md). Необходимо зарегистрировать VSPackage с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], который также требуются административные учетные данные.  
  
 Администраторы имеют полные права доступа для записи в реестре и файловой системе, а также для выполнения любого кода. Необходимо иметь следующие разрешения для разработки, развертывания или установки пакетов VSPackage.  
  
 Как только установки VSPackage является полностью доверенным. Из-за высокий уровень разрешений, связанных с VSPackage существует возможность случайно установить пакет VSPackage, который злоумышленников.  
  
 Пользователям следует убедиться, что они установку пакетов VSPackage только из доверенных источников. Компании разработка пакетов VSPackage должен строго имени и подпишите их, для обеспечения предсказуемой, незаконное изменение запрещено. Разработка пакетов VSPackage компаниям следует проверить их внешние зависимости, такие как веб-службы и удаленной установки, чтобы оценить и устранить все проблемы безопасности.  
  
 Дополнительные сведения см. в разделе [правила написания безопасного кода для .NET Framework](http://msdn.microsoft.com/library/d55zzx87.aspx).  
  
## <a name="see-also"></a>См. также  
 [Добавить в систему безопасности](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Безопасность DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)