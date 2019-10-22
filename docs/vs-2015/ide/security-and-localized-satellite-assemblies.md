---
title: Безопасность и локализованные вспомогательные сборки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672913"
---
# <a name="security-and-localized-satellite-assemblies"></a>Безопасность и локализованные вспомогательные сборки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если в основной сборке используются строгие имена, вспомогательные сборки должны быть подписаны тем же закрытым ключом, что и основная сборка. Если в основной и вспомогательных сборках используются разные пары из открытого и закрытого ключей, ресурсы не будут загружены. Дополнительные сведения о подписывании сборок см. в разделе [Практическое руководство. Подписание сборки строгим именем](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 В общем случае может потребоваться закрытый ключ группы подписи собственной или внешней подписывающей организации. Причина заключается в конфиденциальном характере закрытого ключа: доступ к нему часто ограничивается несколькими лицами. Во время разработки можно использовать отложенную подпись. Дополнительные сведения см. в разделе [Отложенная подпись сборки](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).

## <a name="see-also"></a>См. также
 [Вопросы безопасности сборки основные](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) [понятия безопасности](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) [Введение в международные приложения на основе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [локализации приложений](../ide/localizing-applications.md) [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
