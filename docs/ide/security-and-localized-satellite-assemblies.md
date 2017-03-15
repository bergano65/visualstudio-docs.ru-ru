---
title: "Безопасность и локализованные вспомогательные сборки | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 587b403257a5fadefd32e57ecdd9914bd60a9e26
ms.lasthandoff: 02/22/2017

---
# <a name="security-and-localized-satellite-assemblies"></a>Безопасность и локализованные вспомогательные сборки
Если в основной сборке используются строгие имена, вспомогательные сборки должны быть подписаны тем же закрытым ключом, что и основная сборка. Если в основной и вспомогательных сборках используются разные пары из открытого и закрытого ключей, ресурсы не будут загружены. Дополнительные сведения о подписывании сборок см. в разделе [Практическое руководство. Подписание сборки строгим именем](http://msdn.microsoft.com/Library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 В общем случае может потребоваться закрытый ключ группы подписи собственной или внешней подписывающей организации. Причина заключается в конфиденциальном характере закрытого ключа: доступ к нему часто ограничивается несколькими лицами. Во время разработки можно использовать отложенную подпись. Дополнительные сведения см. в разделе [Отложенная подпись сборки](http://msdn.microsoft.com/Library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности сборок](http://msdn.microsoft.com/Library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Основные понятия безопасности](http://msdn.microsoft.com/Library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
