---
title: Отключение предупреждений с помощью атрибута SuppressMessage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8df4972cb1d54b88d6e716254574ea95bcaed4b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672440"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Подавление предупреждений при помощи атрибута SuppressMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Часто бывает полезно указать, что предупреждение неприменимо, чтобы члены команды могли понять, что код был проверен, и было определено, что предупреждение должно быть подавлено. Подавление исходного кода (ISS) позволяет разработчику разместить атрибут, который подавляет предупреждение ближе к расположению, вызвавшему предупреждение. Вы можете добавить атрибут ISS непосредственно в исходный файл или использовать контекстное меню в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.

## <a name="in-this-section"></a>Содержание

|||
|-|-|
|[Общие сведения о подавлении в исходном коде](../code-quality/in-source-suppression-overview.md)|Узнайте о ISS и о том, как использовать его в коде.|
|[Практическое руководство. Отключение предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Сведения о подавлении предупреждений в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE с помощью контекстного меню.|

## <a name="related-sections"></a>Связанные разделы
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
