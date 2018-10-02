---
title: Развертывание типов проектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66069ac71fbe59e8b63126d66d2a0cc63ed095bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562062"
---
# <a name="deploying-project-types"></a>Развертывание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [развертывание типов проектов](https://docs.microsoft.com/visualstudio/extensibility/internals/deploying-project-types).  
  
[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Устанавливает агрегатор новый тип проекта (ProjectAggregator2.dll), а также пакет установщика Windows для распространения (ProjectAggregator2.msi). Необходимо использовать новые средства инвентаризации программного обеспечения для типов проектов управляемого кода. ProjectAggregator2 работает способы ограничения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проект средства инвентаризации программного обеспечения, которые препятствовать правильной работе типы проектов управляемого кода. Далее описано изменение VSPackage для использования нового средства инвентаризации программного обеспечения.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите NativeHierarchyWrapper двоичные файлы из пакета установки.  
  
3.  Добавьте ProjectAggregator2.msi на настройки.

