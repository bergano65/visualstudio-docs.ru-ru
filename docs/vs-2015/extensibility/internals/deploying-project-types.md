---
title: Развертывание типов проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196882"
---
# <a name="deploying-project-types"></a>Развертывание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Устанавливает агрегатор новый тип проекта (ProjectAggregator2.dll), а также пакет установщика Windows для распространения (ProjectAggregator2.msi). Необходимо использовать новые средства инвентаризации программного обеспечения для типов проектов управляемого кода. ProjectAggregator2 работает способы ограничения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проект средства инвентаризации программного обеспечения, которые препятствовать правильной работе типы проектов управляемого кода. Далее описано изменение VSPackage для использования нового средства инвентаризации программного обеспечения.  
  
1. Удалите NativeHierarchyWrapper проект из решения.  
  
2. Удалите NativeHierarchyWrapper двоичные файлы из пакета установки.  
  
3. Добавьте ProjectAggregator2.msi на настройки.
