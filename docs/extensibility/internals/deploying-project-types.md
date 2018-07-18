---
title: Развертывание проекта типов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127980"
---
# <a name="deploying-project-types"></a>Развертывание проекта типов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Устанавливает агрегатор новый тип проекта (ProjectAggregator2.dll), а также пакет установщика Windows для распространения (ProjectAggregator2.msi). Новому средству необходимо использовать для типов управляемых проектов. ProjectAggregator2 работает способы ограничения в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта инвентаризации программного обеспечения, которые препятствуют правильной работе типы проектов управляемого кода. Следующие шаги описывают изменения VSPackage для использования новому средству.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите все двоичные файлы NativeHierarchyWrapper из установки.  
  
3.  Добавьте ProjectAggregator2.msi к установке.