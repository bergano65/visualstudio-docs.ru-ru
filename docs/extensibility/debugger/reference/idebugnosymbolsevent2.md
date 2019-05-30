---
title: IDebugNoSymbolsEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadd4547d5b0f691b454a98ba714abea9bf6f058
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323718"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Сигналы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика пользовательского интерфейса, чтобы предупредить пользователя, что символы не удалось найти для запущенный исполняемый файл.

## <a name="syntax"></a>Синтаксис

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуется отладчиков и потребляемых [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика пользовательского интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll