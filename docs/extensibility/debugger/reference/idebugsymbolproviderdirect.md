---
title: IDebugSymbolProviderDirect (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718906"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Представляет поставщика символов, который имеет прямой доступ к метаданным и интерфейсам основных символов.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Извлекает идентификатор домена приложения с учетом адреса отладки.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Извлекает информацию о модулях в группе символов.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Извлекает информацию о группе символов, членом которой является поставщик символов.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Извлекает информацию об импорте метаданных.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Извлекает информацию о методе по указанному адресу отладки.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Извлекает считыватель символов для неуправляемого кода.|

## <a name="remarks"></a>Примечания
 Этот интерфейс можно использовать вместо большинства других интерфейсов поставщика символов. Он обеспечивает прямой доступ к `CorSym` метаданным и интерфейсам.

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
