---
title: Создание подключаемого подключения к управлению исходным элементом (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709172"
---
# <a name="create-a-source-control-plug-in"></a>Создание плагина управления исходным элементом
Visual Studio SDK предоставляет ресурсы, позволяющие добавлять [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возможности управления исходными данными в интегрированную среду разработки (IDE). Он позволяет использовать любой плагин DLL, который соответствует API-разъему управления исходным элементом, изложенным в настоящей документации.

## <a name="in-this-section"></a>В этом разделе
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Описывает, как установить плагин управления исходным управлением и выделяет доступные в настоящее время версии API управления исходным управлением.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 Использует диаграмму архитектуры для объяснения интеграции плагина [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управления исходным управлением с IDE.

- [Руководство по тестированию](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Предоставляет рекомендации о том, как проверить установку и эксплуатацию плагина управления исходным управлением.

## <a name="related-sections"></a>См. также
- [Создание управления исходным элементом VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Обсуждается, как создать элемент управления исходным источником VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] который не только поставляет функциональность управления исходным источником, но и заменяет uI управления исходным управлением.

- [Плагины управления исходным элементом](../../extensibility/source-control-plug-ins.md)

 Предоставляет полный список всех элементов в API для управления исходным управлением.

- [Управление исходом](../../extensibility/internals/source-control.md)

 Обсуждается варианты реализации управления исходным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]источником в качестве интегрированной функции .
