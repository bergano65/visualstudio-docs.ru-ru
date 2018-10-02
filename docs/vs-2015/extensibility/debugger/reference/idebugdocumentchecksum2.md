---
title: IDebugDocumentChecksum2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e6d3428b5091841f0229b146c9e086ceb208d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570562"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDocumentChecksum2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentchecksum2).  
  
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

