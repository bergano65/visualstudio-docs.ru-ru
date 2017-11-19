---
title: "IDebugSymbolProviderDirect | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 077a4422d7e8edde460e03dd2a26675df3fdd6fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Представляет поставщик символ, который имеет прямой доступ к метаданных и основных интерфейсов символов.  
  
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
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Извлекает сведения о группе символов, членом которого является символ поставщика.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Извлекает сведения о импорта метаданных.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Извлекает сведения о методе по адресу указанного отладки.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Возвращает средство чтения символов для неуправляемого кода.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс может использоваться вместо большинство интерфейсов поставщика символов. Он предоставляет прямой доступ к метаданным и `CorSym` интерфейсов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll