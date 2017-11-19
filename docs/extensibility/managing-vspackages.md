---
title: "Управление пакетов VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55ba59a5a29181dfa3cdd70427720293582a648d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="managing-vspackages"></a>Управление пакетов VSPackage
В большинстве случаев не нужно беспокоиться об управлении пакеты VSPackage, так как шаблоны проектов и элементов регистрации и автоматически загрузить пакет. Однако в некоторых случаях может потребоваться узнать дополнительные бит для пакета управления.  
  
## <a name="using-the-experimental-instance"></a>С помощью экспериментальный экземпляр  
 Дополнительные сведения о экспериментальный экземпляр, в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Регистрация и Отмена регистрации пакетов VSPackage  
 Чтобы узнать, как регистрировать и отменять регистрацию пакеты VSPackage и другими типами расширений, в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Загрузка VSPackage  
 Пакеты VSPackage может устанавливаться для автозагрузки (AutoLoad) при определенной CMDUICONTEXT GUID будет включена. Дополнительные сведения см. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>С помощью AsyncPackage для загрузки пакетов VSPackage в фоновом режиме  
 Класс AsyncPackage позволяет пакету, загрузку в фоновом потоке, для повышения скорости отклика пользовательского интерфейса в Visual Studio. Дополнительные сведения см. в разделе [как: AsyncPackage используется для загрузки пакетов VSPackage в фоновом режиме](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Контекст пользовательского интерфейса на основе правил для расширения  
 Контексты пользовательского интерфейса на основе правил позволяет авторам расширения определить точные условия, при которых активируется контекста пользовательского интерфейса и загрузить связанные пакеты VSPackage. Дополнительные сведения см. в разделе [как: на основе правила использования контекста пользовательского интерфейса для расширений Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Диагностика производительности расширения  
Расширения могут повлиять на производительность нагрузки запуска и решения. Узнайте, как вычисляется влияние расширения Visual Studio и как их можно проанализировать локально для проверки, если расширение может отображаться как расширения, влияющие на производительность. Дополнительные сведения см. в разделе [как: диагностики производительности расширение](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Устранение неполадок пакетов VSPackage  
 Узнайте, методы устранения неполадок пакетов VSPackage, не загружать или возникли ошибки: [пакеты VSPackage, устранение неполадок](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)