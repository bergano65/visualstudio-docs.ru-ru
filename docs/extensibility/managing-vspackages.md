---
title: "Управление VSPackages | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>Управление пакеты VSPackage
В большинстве случаев не нужно беспокоиться об управлении VSPackages, поскольку Регистрация шаблонов проектов и элементов и автоматически загрузить пакет. Однако в некоторых случаях может потребоваться узнать чуть подробнее для пакета управления.  
  
## <a name="using-the-experimental-instance"></a>С помощью экспериментальный экземпляр  
 Чтобы узнать больше о экспериментальный экземпляр, в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Регистрация и Отмена регистрации VSPackages.  
 Чтобы узнать, как регистрировать и отменять регистрацию VSPackages и другими типами расширений, см. раздел [регистрация и Отмена регистрации VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Загрузки VSPackage  
 Можно задать VSPackages для автозагрузки, когда конкретного CMDUICONTEXT GUID будет включена. Дополнительные сведения см. в разделе [загрузки пакетов VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>С помощью AsyncPackage для загрузки пакетов VSPackages в фоновом режиме  
 Класс AsyncPackage пакет загрузку в фоновом потоке, для повышения скорости отклика пользовательского интерфейса в Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство: использование AsyncPackage для загрузки пакетов VSPackages в фоновом режиме](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Контекст пользовательского интерфейса на основе правил для расширения  
 Контексты пользовательского интерфейса на основе правил позволяет авторам расширения определить точные условия, при которых активируется контекста пользовательского интерфейса и загрузить связанные пакеты VSPackage. Дополнительные сведения см. в разделе [как: на основе правил использования контекст пользовательского интерфейса для расширения Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Диагностика производительности расширения  
Расширения могут повлиять на производительность нагрузки запуска и решений. Узнайте, как вычисляется влияние расширения Visual Studio и как их можно проанализировать локально для тестирования, если расширение может отображаться как расширения, влияющие на производительность. Дополнительные сведения см. в разделе [как: Диагностика производительности расширение](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Устранение неполадок пакетов VSPackages  
 Узнайте, методы устранения неполадок пакетов VSPackages, не загружаются или в случае ошибки: [пакеты VSPackage, устранение неполадок](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
