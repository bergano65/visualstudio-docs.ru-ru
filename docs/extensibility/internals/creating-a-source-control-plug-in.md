---
title: Создание подключаемого модуля системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709172"
---
# <a name="create-a-source-control-plug-in"></a>Создание подключаемого модуля системы управления версиями
Пакет SDK для Visual Studio предоставляет ресурсы, позволяющие добавлять возможности системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированную среду разработки (IDE). Он позволяет использовать любую подключаемую библиотеку DLL, которая соответствует интерфейсу API подключаемого модуля системы управления версиями, описанному в этой документации.

## <a name="in-this-section"></a>В этом разделе
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Описывает, как установить подключаемый модуль системы управления версиями и выделить доступные в настоящее время версии API подключаемого модуля системы управления версиями.

- [Архитектура](../../extensibility/internals/source-control-plug-in-architecture.md)

 Использует схему архитектуры для объяснения интеграции подключаемого модуля системы управления версиями с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки.

- [Тестовый обзор](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Содержит рекомендации по тестированию установки и эксплуатации подключаемого модуля системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage для системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность системы управления версиями, но и заменяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс системы управления версиями.

- [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)

 Содержит полный список всех элементов в интерфейсе API подключаемого модуля системы управления версиями.

- [Система управления версиями](../../extensibility/internals/source-control.md)

 Описывает варианты реализации системы управления версиями в качестве интегрированной функции [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
