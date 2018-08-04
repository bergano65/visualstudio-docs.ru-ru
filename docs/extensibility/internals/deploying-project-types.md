---
title: Развертывание типов проектов | Документация Майкрософт
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
ms.openlocfilehash: 4bed37260925d4961ed5b5b7d3e69d55169444ad
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497905"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новые средства инвентаризации программного обеспечения типа проекта (*ProjectAggregator2.dll*) и также пакет установщика Windows для распространения (*ProjectAggregator2.msi*). Необходимо использовать новые средства инвентаризации программного обеспечения для типов проектов управляемого кода. ProjectAggregator2 предназначена для обхода ограничения в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект средства инвентаризации программного обеспечения, которое препятствует правильной работе типы проектов управляемого кода. Далее описано изменение VSPackage для использования нового средства инвентаризации программного обеспечения.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите NativeHierarchyWrapper двоичные файлы из пакета установки.  
  
3.  Добавить *ProjectAggregator2.msi* на настройки.