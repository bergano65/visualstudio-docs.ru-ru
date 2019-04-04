---
title: Справочник по API для расширения моделей UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12eadb9844df5da78b11367708fed715f1c13672
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991111"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Справочник по API для расширения моделей UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете написать программный код для чтения и изменения моделей, созданных с помощью Visual Studio. Справочник по API содержит информацию об определенных классах, помогающих справиться с этой задачей. Дополнительные сведения, ориентированные на задачи, см. в подразделах раздела [моделей и схем UML, расширение](../modeling/extend-uml-models-and-diagrams.md). Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Сборки  
  
|Assembly|Возможности|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|— Чтение и изменение элементов модели, например IUseCase, IAssociation и т. д.<br />— Переход по связям между элементами.<br /><br /> Пространства имен и типы соответствуют пространствам имен и типам, которые определены в спецификации UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Создание новых экземпляров элементов модели<br />-Доступ и изменение фигур и схем.|  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Справка по API SDK моделирования для Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
