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
ms.openlocfilehash: 9668336c565b4a3be332509d1c960b067a486785
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583636"
---
# <a name="vscodewindowmanager-object"></a>Объект Вскодевиндовманажер

Языковая служба реализует диспетчер окон кода и отвечает за управление декоративными элементами (например, с помощью раскрывающейся панели). Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

В следующей таблице показаны интерфейсы в `VSCodeWindowManager` объекте.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Позволяет добавлять в окно кода декоративные элементы (такие как раскрывающиеся полосы).|