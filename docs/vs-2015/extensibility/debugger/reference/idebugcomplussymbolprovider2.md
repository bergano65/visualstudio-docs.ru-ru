---
title: IDebugComPlusSymbolProvider2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 868528d5fd7d54f0a515a32895646b0cb94b26ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186482"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет поставщик символов COM+ с методами, специфичными для управляемого кода, и расширяет[Идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) **идебугкомплуссимболпровидер**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам в интерфейсе [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Определяет, содержит ли указанный метод сведения о строке.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Извлекает тип по заданному имени.|  
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Извлекает тип с учетом его токена.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Определяет, является ли указанный адрес отладки точкой следования.|  
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Загружает отладочные символы с помощью указанного метода обратного вызова.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Загрузка отладочных символов из потока данных по заданному объекту **ICorDebugModule** .|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Загружает символы отладки по заданному объекту **ICorDebugModule** .|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
