---
title: "Развертывание типы проектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проекты [Visual Studio SDK] управляемого кода"
  - "проекты [Visual Studio SDK] агрегации"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Развертывание типы проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Устанавливает агрегатор новый тип проекта \(ProjectAggregator2.dll\), а также пакет установщика Windows для распространения \(ProjectAggregator2.msi\). Необходимо использовать новый статистическую функцию для типов управляемых проектов. ProjectAggregator2 работает способы ограничения в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта агрегатора, препятствующих правильной работе типов управляемых проектов. Ниже описывается изменение VSPackage для использования нового агрегатора.  
  
1.  Удалите NativeHierarchyWrapper проект из решения.  
  
2.  Удалите NativeHierarchyWrapper двоичные файлы из установки.  
  
3.  Добавьте ProjectAggregator2.msi к установке.