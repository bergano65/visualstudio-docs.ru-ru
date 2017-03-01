---
title: "Устранение неполадок расширений для схем зависимостей | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Устранение неполадок расширений для схем зависимостей
В этом разделе рассматриваются некоторые проблемы, которые могут возникнуть при создании расширений модели слоев.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>При нажатии клавиши F5 для отладки расширения, команды, обработчики жестов, расширения проверки или пользовательские свойства не отображаются на схемах зависимостей в экспериментальном экземпляре[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Откройте решение расширения в экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и на **построения** меню, щелкните **Перестроить решение**.  
  
2.  Нажмите клавишу **F5** или **CTRL + F5** Чтобы запустить экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Откройте диаграмму зависимостей и протестируйте расширение.  
  
 При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Запускается старая версия расширения.  
  
1.  Убедитесь в том, что не выполняется экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Удалите следующую папку: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [версия]  
  
    > [!NOTE]
    >  % LocalAppData % — *DriveName*: \Users\\*UserName*\AppData\Local.  
  
 При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Отображается старая версия результатов проверки, либо не вызывается метод проверки.  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]на **построения** меню, щелкните **Очистить решение**. Она позволяет очистить кэшированные результаты предыдущего анализа проверки.  
  
2.  Убедитесь в том, что слои в модели связаны с элементами кода и что в модели есть хотя бы одна связь зависимости. Проверка не вызывается, если нет элементов для проверки.  
  
3.  Стандартные точки останова могут не работать в методе проверки, так как он выполняется в отдельном процессе. Для пошагового выполнения метода нужно вставить вызов метода `System.Diagnostics.Debugger.Launch()`.  
  
4.  В **source.extension.vsixmanifest** проекта проверки слоев, убедитесь, что добавлены **компонент MEF** элемента и **пользовательский тип расширения** раздел **содержимого**.  
  
## <a name="see-also"></a>См. также  
 [Расширение схемы зависимостей](../modeling/extend-layer-diagrams.md)

