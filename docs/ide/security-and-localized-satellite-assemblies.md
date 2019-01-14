---
title: Безопасность и локализованные вспомогательные сборки
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d0c38ae4353c7761b1cff4173b995ab6c89e0a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892057"
---
# <a name="security-and-localized-satellite-assemblies"></a>Безопасность и локализованные вспомогательные сборки

Если в основной сборке используются строгие имена, вспомогательные сборки должны быть подписаны тем же закрытым ключом, что и основная сборка. Если в основной и вспомогательных сборках используются разные пары из открытого и закрытого ключей, ресурсы не будут загружены. Дополнительные сведения о подписывании сборок см. в разделе [Практическое руководство. Подписание сборки строгим именем](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 В общем случае может потребоваться закрытый ключ группы подписи собственной или внешней подписывающей организации. Причина заключается в конфиденциальном характере закрытого ключа: доступ к нему часто ограничивается несколькими лицами. Во время разработки можно использовать отложенную подпись. Дополнительные сведения см. в разделе [Отложенная подпись сборки](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>См. также

- [Вопросы безопасности сборок](/dotnet/framework/app-domains/assembly-security-considerations)  - [Основные понятия безопасности](/dotnet/standard/security/key-security-concepts)
- [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Локализация приложений](../ide/localizing-applications.md)
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)