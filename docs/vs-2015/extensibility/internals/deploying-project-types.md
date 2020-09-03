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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196882"
---
# <a name="deploying-project-types"></a>Развертывание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] устанавливает новый агрегатор типа проекта (ProjectAggregator2.dll), а также пакет установщик Windows для распространения (ProjectAggregator2.msi). Для типов проектов с управляемым кодом необходимо использовать новый агрегатор. ProjectAggregator2 взаимодействует с ограничениями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] агрегаторе проекта, которые препятствуют правильной работе типов проектов управляемого кода. Следующие шаги описывают, как изменить пакет VSPackage для использования новой агрегаторы.  
  
1. Удалите проект Нативехиерарчивраппер из решения.  
  
2. Удалите из программы установки все двоичные файлы Нативехиерарчивраппер.  
  
3. Добавьте ProjectAggregator2.msi в программу установки.
