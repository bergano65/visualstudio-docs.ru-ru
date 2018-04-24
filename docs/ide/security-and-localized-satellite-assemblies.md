---
title: Безопасность и локализованные вспомогательные сборки | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
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
ms.openlocfilehash: ca89e842b6e5229890e93c06b7ca83658f6dbf7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="security-and-localized-satellite-assemblies"></a>Безопасность и локализованные вспомогательные сборки

Если в основной сборке используются строгие имена, вспомогательные сборки должны быть подписаны тем же закрытым ключом, что и основная сборка. Если в основной и вспомогательных сборках используются разные пары из открытого и закрытого ключей, ресурсы не будут загружены. Дополнительные сведения о подписывании сборок см. в разделе [Практическое руководство. Подписание сборки строгим именем](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 В общем случае может потребоваться закрытый ключ группы подписи собственной или внешней подписывающей организации. Причина заключается в конфиденциальном характере закрытого ключа: доступ к нему часто ограничивается несколькими лицами. Во время разработки можно использовать отложенную подпись. Дополнительные сведения см. в разделе [Отложенная подпись сборки](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>См. также

- [Вопросы безопасности сборок](/dotnet/framework/app-domains/assembly-security-considerations)  - [Основные понятия безопасности](/dotnet/standard/security/key-security-concepts)   
- [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
- [Локализация приложений](../ide/localizing-applications.md)   
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)