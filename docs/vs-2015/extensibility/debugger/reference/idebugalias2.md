---
title: IDebugAlias2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2349203c49bc164bb3af6bcf51e39afb56022be0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991708"
---
# <a name="idebugalias2"></a>IDebugAlias2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовые псевдоним для переменной и обеспечивает вычислитель выражений (EE), чтобы получить домен приложения для псевдонима.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется Подсистема управляемой отладки (DE).  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Извлекает идентификатор для домена приложения.|  
  
## <a name="remarks"></a>Примечания  
 Псевдоним — это десятичное число в виде строки, за которым следует символ #, к примеру, 1001#.  
  
## <a name="requirements"></a>Требования  
 Заголовок: EE.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
