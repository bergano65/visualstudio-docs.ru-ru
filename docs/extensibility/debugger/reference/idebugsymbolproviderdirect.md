---
title: IDebugSymbolProviderDirect | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64cab3dde38f3008a097e89b17b2d61921332ed6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965318"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Представляет поставщик символ, который имеет прямой доступ к интерфейсам символ метаданных и core.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Извлекает идентификатор домена приложения, указанного адреса отладки.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Извлекает сведения о модулях в группе символов.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Извлекает сведения о группе символов, членом которой является поставщик символов.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Извлекает сведения о импорта метаданных.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Извлекает сведения о методе по адресу указанного отладки.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Получает средство чтения символов для неуправляемого кода.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс может использоваться вместо большую часть интерфейсы поставщика символов. Он обеспечивает прямой доступ к метаданным и `CorSym` интерфейсов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll