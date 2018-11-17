---
title: IDebugTypeFieldBuilder2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb3076e82ecdb4f9bf57d76706ebd9f83ab3b722
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745475"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Расширяет **IDebugTypeFieldBuilder** чтобы иметь возможность создавать типы массивов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс можно получить от поставщика символов.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Создает массив указанного типа и размера.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

