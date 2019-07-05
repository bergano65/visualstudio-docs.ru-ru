---
title: Рекомендации по безопасности в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 144bc62176ebc552e7070b29088acf70329a84d4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309159"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по обеспечению безопасности в пакетах VSPackage
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] на компьютере, необходимо использовать в контексте от имени администратора. Базовая единица безопасность и развертывание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] приложение [VSPackage](../../extensibility/internals/vspackages.md). Необходимо зарегистрировать VSPackage с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], который также требуются административные учетные данные.

 Администраторы имеют полные права доступа для записи в реестре и файловой системе, а также для выполнения любого кода. Необходимо иметь следующие разрешения для разработки, развертывания или установки пакетов VSPackage.

 Как только установки VSPackage является полностью доверенным. Из-за высокий уровень разрешений, связанных с VSPackage существует возможность случайно установить пакет VSPackage, который злоумышленников.

 Пользователям следует убедиться, что они установку пакетов VSPackage только из доверенных источников. Компании разработка пакетов VSPackage должен строго имени и подпишите их, для обеспечения предсказуемой, незаконное изменение запрещено. Разработка пакетов VSPackage компаниям следует проверить их внешние зависимости, такие как веб-службы и удаленной установки, чтобы оценить и устранить все проблемы безопасности.

 Дополнительные сведения см. в разделе [правила написания безопасного кода для .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>См. также
- [Добавить в систему безопасности](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Безопасность DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)