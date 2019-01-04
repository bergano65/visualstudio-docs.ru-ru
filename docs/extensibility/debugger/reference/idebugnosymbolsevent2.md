---
title: IDebugNoSymbolsEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 179d8a95bc54db90a98311626b34c3e17b68f7f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873123"
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