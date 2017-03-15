---
title: "Перенос, миграция и обновление проектов Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4
ms.lasthandoff: 02/22/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Перенос, миграция и обновление проектов Visual Studio
Если вы принимаете решение о том, следует ли переходить на новую версию Visual Studio, вы хотите знать, нужно ли вносить изменения в решения, проекты, файлы и другие активы, созданные в более ранних версиях, *перед* их запуском в последних версиях.

 Многие часто используемые активы работают одинаково в последней версии-кандидате Visual Studio 2017 и в недавней версии Visual Studio 2015. То же самое верно для более ранних версий — Visual Studio 2013 и Visual Studio 2012.

 Например, в версии-кандидате Visual Studio 2017 можно открыть проект, созданный в Visual Studio 2015 или Visual Studio 2013, изменить его, а затем снова открыть его в версии-кандидате Visual Studio 2017; изменения сохраняются, и проект ведет себя так же, как и в более ранней версии. То же самое верно для многих других активов, созданных в Visual Studio 2012.  

 При использовании Visual Studio 2015 вместе с Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1) можно создавать и изменять проекты и файлы в любой из этих версий. Проекты и файлы можно перемещать между версиями, если не добавлять компоненты, которые не поддерживаются одной из версий. (Дополнительные сведения о возможностях, относящихся к конкретным версиям, см. в статье [Заметки о выпуске](https://www.visualstudio.com/vs/release-notes/).)

