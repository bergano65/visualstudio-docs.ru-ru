---
title: IDebugDocumentHelper::D Ефинескриптблокк | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576982"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Указывает вспомогательному модулю, что определенный диапазон символов является блоком сценария, который обрабатывается заданным обработчиком скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ulCharOffset`  
 окне Расположение начала блока скрипта.  
  
 `cChars`  
 окне Число символов в блоке скрипта.  
  
 `pas`  
 окне Обработчик скриптов для этого блока сценария.  
  
 `fScriptlet`  
 окне Флаг, указывающий, является ли блок скрипта скриптлет.  
  
 `pdwSourceContext`  
 заполняет Контекст источника для блока скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Направляющий узел может использовать этот метод, если его документы содержат внедренные блоки скриптов. Языковой механизм может использовать этот метод, если его код содержит внедренные скрипты для других языков.  
  
 Обработчик скриптов отвечает за все выкраски синтаксиса и поиск контекста кода в блоке script.  
  
 Метод `DefineScriptBlock` должен вызываться после добавления текста (например, с помощью метода `IDebugDocumentHelper::AddDBCSText`), но перед синтаксическим анализом блока скрипта (например, с помощью метода `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: адддбкстекст](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)