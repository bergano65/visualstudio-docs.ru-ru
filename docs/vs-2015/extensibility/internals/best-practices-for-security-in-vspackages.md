---
title: Рекомендации по обеспечению безопасности в VSPackage | Документация Майкрософт
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
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697270"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по обеспечению безопасности при использовании пакетов VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы установить [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] на компьютере, необходимо работать в контексте с административными учетными данными. Основной единицей безопасности и развертывания [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] приложения являются [пакеты VSPackage](../../extensibility/internals/vspackages.md). Пакет VSPackage должен быть зарегистрирован с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , который также требует учетных данных администратора.  
  
 Администраторы имеют полные разрешения на запись в реестр и файловую систему, а также на выполнение любого кода. Эти разрешения необходимы для разработки, развертывания или установки пакета VSPackage.  
  
 Как только оно будет установлено, VSPackage будет полностью доверенным. Из-за такого высокого уровня разрешений, связанных с VSPackage, можно случайно установить пакет VSPackage, имеющий вредоносную намерение.  
  
 Пользователи должны убедиться, что они устанавливают пакеты VSPackage только из надежных источников. Компании, разрабатывающих пакеты VSPackage, должны строго присвоить имя и подписать их, чтобы предотвратить фальсификацию пользователя. Компании, разрабатывающих пакеты VSPackage, должны исследовать свои внешние зависимости, такие как веб-службы и удаленная установка, для анализа и устранения любых проблем безопасности.  
  
 Дополнительные сведения см. в разделе рекомендации по безопасному кодированию для .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>См. также:  
 [Безопасность надстроек](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Безопасность DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
