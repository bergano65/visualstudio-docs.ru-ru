---
title: Справочник по API для расширения моделей UML | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: db042d59ce5f7363d9ed45e2baebbea45d3a0de4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568296"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Справочник по API для расширения моделей UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Справочник по API для расширения моделей UML](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility).  
  
Вы можете написать программный код для чтения и изменения моделей, созданных с помощью Visual Studio. Справочник по API содержит информацию об определенных классах, помогающих справиться с этой задачей. Дополнительные сведения, ориентированные на задачи, см. в подразделах раздела [моделей и схем UML, расширение](../modeling/extend-uml-models-and-diagrams.md). Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Сборки  
  
|Сборка|Возможности|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|— Чтение и изменение элементов модели, например IUseCase, IAssociation и т. д.<br />— Переход по связям между элементами.<br /><br /> Пространства имен и типы соответствуют пространствам имен и типам, которые определены в спецификации UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Создание новых экземпляров элементов модели<br />-Доступ и изменение фигур и схем.|  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Справка по API SDK моделирования для Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



