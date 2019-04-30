---
title: Устранение неполадок с расширениями для схем слоев | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 38a459760dd66e1160bd8b197ee9883b617639b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439753"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Устранение неполадок, связанных с расширениями для схем слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе рассматриваются некоторые проблемы, которые могут возникнуть при создании расширений модели слоев.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>При нажатии клавиши F5 для отладки расширения команды, обработчики жестов, расширения проверки или пользовательские свойства не отображаются на схемах слоев в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
1. Откройте решение расширения в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], а затем на **построения** меню, щелкните **Перестроить решение**.  
  
2. Нажмите клавишу **F5** или **CTRL + F5** запустить экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Откройте схему слоев и протестируйте расширение.  
  
   При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Запускается старая версия расширения.  
  
1. Убедитесь в том, что не выполняется экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Удалите следующую папку: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [версия]  
  
   > [!NOTE]
   > % LocalAppData % — *DriveName*: \Users\\*UserName*\AppData\Local.  
  
   При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Отображается старая версия результатов проверки, либо не вызывается метод проверки.  
  
1. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]на **построения** меню, щелкните **Очистить решение**. Она позволяет очистить кэшированные результаты предыдущего анализа проверки.  
  
2. Убедитесь в том, что слои в модели связаны с элементами кода и что в модели есть хотя бы одна связь зависимости. Проверка не вызывается, если нет элементов для проверки.  
  
3. Стандартные точки останова могут не работать в методе проверки, так как он выполняется в отдельном процессе. Для пошагового выполнения метода нужно вставить вызов метода `System.Diagnostics.Debugger.Launch()`.  
  
4. В **source.extension.vsixmanifest** проекта проверки слоев убедитесь, что добавлены оба **компонент MEF** элемента и **пользовательский тип расширения** в меню **Содержимого**.  
  
## <a name="see-also"></a>См. также  
 [Расширение схем слоев](../modeling/extend-layer-diagrams.md)
