---
title: Объект Вскодевиндовманажер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fea97c8784402c55947c108f42f2f3153f322d9c
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012390"
---
# <a name="vscodewindowmanager-object"></a>Объект Вскодевиндовманажер

Языковая служба реализует диспетчер окон кода и отвечает за управление декоративными элементами (например, с помощью раскрывающейся панели). Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

В следующей таблице показаны интерфейсы в `VSCodeWindowManager` объекте.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Позволяет добавлять в окно кода декоративные элементы (такие как раскрывающиеся полосы).|