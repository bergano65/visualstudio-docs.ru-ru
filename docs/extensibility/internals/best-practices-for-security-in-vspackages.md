---
title: Рекомендации по обеспечению безопасности в VSPackages (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709908"
---
# <a name="best-practices-for-security-in-vspackages"></a>Рекомендации по безопасности в VSPackages
Чтобы установить [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] компьютер, необходимо работать в контексте с административными учетными данными. Основным блоком [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] безопасности и развертывания приложения является [VSPackage.](../../extensibility/internals/vspackages.md) VSPackage должен быть зарегистрирован [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]с помощью, который также требует административных учетных данных.

 Администраторы имеют полное разрешение на запись в реестр и файловую систему, а также на запуск любого кода. Вы должны иметь эти разрешения для разработки, развертывания или установки VSPackage.

 Как только он установлен, VSPackage полностью доверяют. Из-за такого высокого уровня разрешения, связанного с VSPackage, можно непреднамеренно установить VSPackage, который имеет злой умысел.

 Пользователи должны убедиться, что они устанавливают VSPackages только из надежных источников. Компании, разрабатывающие VSPackages, должны решительно называть и подписывать их, чтобы убедить пользователя в том, что фальсификация предотвращается. Компании, разрабатывающие VSPackages, должны изучить свои внешние зависимости, такие как веб-сервисы и удаленная установка, для оценки и исправления любых проблем безопасности.

 Для получения дополнительной информации [см.](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))

## <a name="see-also"></a>См. также
- [Безопасность надстройки](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Безопасность DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
