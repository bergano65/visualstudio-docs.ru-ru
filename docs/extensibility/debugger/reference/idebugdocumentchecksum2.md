---
title: IDebugDocumentChecksum2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b40129cb8623e6ea68babe2c480da4e4d4198f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921601"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет контрольную сумму для документа отладки и обеспечивает передачи контрольную сумму между компонентами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс может быть реализован любой компонент, предоставляющий [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс. Тем не менее она главным образом реализуется отладчиков, чтобы контрольная сумма, внедренных в файл символов (*.pdb) могут передаваться обратно в интегрированной среде разработки и используется при поиске источника.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugDocumentChecksum2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Извлекает идентификатор документа контрольной суммы и алгоритм Получает максимальное число байтов для использования.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
