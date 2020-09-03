---
title: IDebugTypeFieldBuilder2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96241026afff71c061abcfae3547d25cc2166902
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152879"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Расширяет **идебугтипефиелдбуилдер** , чтобы иметь возможность создавать типы массивов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс можно получить от поставщика символов.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам в интерфейсе [идебугтипефиелдбуилдер](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Создает массив указанного типа и размера.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
