---
title: "Развертывание проекта типов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2171a940951d828df358d09dae5fec68b6475e4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-project-types"></a>Развертывание проекта типов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Устанавливает агрегатор новый тип проекта (ProjectAggregator2.dll), а также пакет установщика Windows для распространения (ProjectAggregator2.msi). Новому средству необходимо использовать для типов управляемых проектов. ProjectAggregator2 работает способы ограничения в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта инвентаризации программного обеспечения, которые препятствуют правильной работе типы проектов управляемого кода. Следующие шаги описывают изменения VSPackage для использования новому средству.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите все двоичные файлы NativeHierarchyWrapper из установки.  
  
3.  Добавьте ProjectAggregator2.msi к установке.