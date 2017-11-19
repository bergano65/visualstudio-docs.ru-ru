---
title: "IActiveScript::Clone | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Клонирует текущий обработчик скриптов (минус любое текущее состояние выполнения), возврат загрузить обработчик скриптов, у которой нет сайт в текущем потоке. Свойства этот новый обработчик сценариев будет совпадать с заданными свойствами исходный обработчик сценариев будет в, если он был переведен обратно в исходное состояние.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppscript`  
 [out] Адрес переменной, которая получает указатель на [IActiveScript](../../winscript/reference/iactivescript.md) интерфейс клонированного обработчика сценариев. Ведущее приложение должно создать сайт и вызова [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) метод на новый обработчик сценариев, прежде чем он будет в состоянии инициализации и, следовательно, может использоваться.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 `IActiveScript::Clone` Метод является оптимизация `IPersist*::Save`, `CoCreateInstance`, и `IPersist*::Load`, поэтому состояние нового обработчика скриптов должны совпадать как в том случае, если состояние исходный обработчик сценариев были сохранены и загружены в новый обработчик сценариев. Именованные элементы повторяются в клонированной обработчика скриптов, но указателей на объекты, определенные для каждого элемента забыт и получаются с [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) метод. Это позволяет идентичные объектную модель с точки входа каждого потока (модели подразделения) для использования.  
  
 Этот метод используется для многопоточного сервера узлов, которые можно запустить несколько экземпляров и тот же сценарий. Обработчик скриптов может вернуть `E_NOTIMPL`, в этом случае узел достижения того же результата с помощью дублирования постоянное состояние и создания нового экземпляра обработчика скриптов с `IPersist*` интерфейса.  
  
 Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)