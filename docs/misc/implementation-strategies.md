---
title: "Стратегии реализации | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты VSPackage, стратегии реализации"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Стратегии реализации
Можно расширять Visual Studio, добавляя надстройки автоматизации, пакеты VSPackage, компоненты Managed Extensibility Framework \(MEF\) или сочетание этих расширений. Как правило, надстройки проще разрабатывать, но они менее мощные, чем пакеты VSPackage или компоненты MEF. Надстройки могут вызывать интерфейсы расширяемости, а пакеты VSPackage и компоненты MEF могут получать доступ к модели автоматизации Visual Studio. Вы можете объединять несколько разных подходов, чтобы создать эффективное решение.  
  
 Пакеты VSPackage могут быть написаны в неуправляемом или управляемом коде. Рекомендуется создавать новые пакеты VSPackage в управляемом коде с помощью платформы управляемых пакетов \(MPF\). Практически все, что может быть написано в неуправляемом коде, можно реализовать более просто и безопасно в управляемом коде. Тем не менее устаревшие приложения, написанные в неуправляемом коде, продолжат работать в Visual Studio.  
  
 Простые расширения могут добавлять окна инструментов или отправлять сведения в элементы пользовательского интерфейса Visual Studio, такие как строка состояния или окно вывода. Более сложные приложения могут быть написаны как иерархии Visual Studio, такие как обозреватель сервера. Еще больше мощности можно получить путем реализации проекта, редактора или конструктора. Например, сами [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] реализованы как языковые службы.  
  
## Связанные разделы  
 [Пакет SDK для Visual Studio и автоматизация](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Описание использования автоматизации, пакетов VSPackage или их комбинации для создания приложений\-расширений Visual Studio.  
  
 [Пакет SDK для Visual Studio и управляемый код](/visual-cpp/misc/visual-studio-sdk-and-managed-code)  
 Сравнение разных способов создания VSPackage в управляемом коде.  
  
 [Основные понятия IDE Visual Studio](/visual-cpp/misc/visual-studio-ide-concepts)  
 Обсуждение основ пакетов VSPackage и порядка использования службы.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Обсуждение общих элементов пользовательского интерфейса приложения в Visual Studio, таких как окно состояния и окно вывода.  
  
 [Иерархии в Visual Studio](../extensibility/internals/hierarchies-in-visual-studio.md)  
 Обзор иерархий Visual Studio, которые отображаются в интегрированной среде разработки \(IDE\) в виде дерева узлов.  
  
 [Проекты](../extensibility/internals/projects.md)  
 Обзор классов проекта и решения.  
  
 [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md)  
 Описываются способы расширения редактора кода и текстового редактора, а также создания специальных редакторов и конструкторов.  
  
 [Расширяемость устаревших языковой службы](../extensibility/internals/legacy-language-service-extensibility.md)  
 Демонстрируется создание языковых служб.  
  
 [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Справочная документация по VSSDK.  
  
## См. также  
 [Начиная разрабатывать расширения Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md)