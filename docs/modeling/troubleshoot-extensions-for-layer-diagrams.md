---
title: "Устранение неполадок с расширениями для схем зависимостей | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 21a14ed32bb1b63e2363736e438139479ff5bf60
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Устранение неполадок с расширениями для схем зависимостей
В этом разделе рассматриваются некоторые проблемы, которые могут возникнуть при создании расширений модели слоев.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>При нажатии клавиши F5 для отладки расширения, команды, обработчики жестов, расширения проверки и пользовательские свойства не отображаются на схемах зависимостей в экспериментальном экземпляре[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Откройте решение расширения в экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], а затем на **построения** меню, нажмите кнопку **Перестроить решение**.  
  
2.  Нажмите клавишу **F5** или **CTRL + F5** Запуск экспериментального экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Открытие схемы зависимостей и тестирования расширения.  
  
 При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Запускается старая версия расширения.  
  
1.  Убедитесь в том, что не выполняется экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Удалите следующую папку: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [версия]  
  
    > [!NOTE]
    >  % LocalAppData % — *DriveName*: \Users\\*UserName*\AppData\Local.  
  
 При необходимости выполните описанную ниже процедуру.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Отображается старая версия результатов проверки, либо не вызывается метод проверки.  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]на **построения** меню, нажмите кнопку **Очистить решение**. Она позволяет очистить кэшированные результаты предыдущего анализа проверки.  
  
2.  Убедитесь в том, что слои в модели связаны с элементами кода и что в модели есть хотя бы одна связь зависимости. Проверка не вызывается, если нет элементов для проверки.  
  
3.  Стандартные точки останова могут не работать в методе проверки, так как он выполняется в отдельном процессе. Для пошагового выполнения метода нужно вставить вызов метода `System.Diagnostics.Debugger.Launch()`.  
  
4.  В **source.extension.vsixmanifest** в ваш проект проверки слоев, убедитесь в том, как были добавлены **компонент MEF** элемента и **пользовательский тип расширения** элементов в группе **Содержимого**.  
  
## <a name="see-also"></a>См. также  
 [Расширение схем зависимостей](../modeling/extend-layer-diagrams.md)
