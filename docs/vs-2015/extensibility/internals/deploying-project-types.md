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
ms.openlocfilehash: 6f168656950c65ce133a8e808a0fa1232726e1b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979888"
---
# <a name="deploying-project-types"></a>Развертывание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Устанавливает агрегатор новый тип проекта (ProjectAggregator2.dll), а также пакет установщика Windows для распространения (ProjectAggregator2.msi). Необходимо использовать новые средства инвентаризации программного обеспечения для типов проектов управляемого кода. ProjectAggregator2 работает способы ограничения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проект средства инвентаризации программного обеспечения, которые препятствовать правильной работе типы проектов управляемого кода. Далее описано изменение VSPackage для использования нового средства инвентаризации программного обеспечения.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите NativeHierarchyWrapper двоичные файлы из пакета установки.  
  
3.  Добавьте ProjectAggregator2.msi на настройки.
