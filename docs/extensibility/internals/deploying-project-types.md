---
title: Развертывание типов проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708792"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]устанавливает новый агрегатор проектного типа *(ProjectAggregator2.dll*), а также пакет установки Windows для перераспределения *(ProjectAggregator2.msi*). Необходимо использовать новый агрегатор для типов управляемых кодов. ProjectAggregator2 работает вокруг ограничений в агрегаторе [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, который не позволяет управляемым типам кода работать правильно. Ниже описано, как изменить ваш VSPackage, чтобы использовать новый агрегатор.

1. Удалите проект NativeHierarchyWrapper из решения.

2. Удалите любые бинарные файлы NativeHierarchyWrapper из вашей установки.

3. Добавьте *ProjectAggregator2.msi* в настройку.
