---
title: IActiveScript::Clone | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093669"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Клонирует текущий обработчик скриптов (минус любое текущее состояние выполнения), возвращая загружен обработчик скриптов, который у нет сайта в текущем потоке. Свойства этого новый обработчик сценариев будет идентична свойства, которые исходный обработчик сценариев бы в, если он были переведены в состояние, инициализированный.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppscript`  
 [out] Адрес переменной, которая получает указатель на [IActiveScript](../../winscript/reference/iactivescript.md) интерфейс клонированного обработчика скриптов. Ведущее приложение должно создать сайт и вызов [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) метод на новый обработчик скриптов, прежде чем он станет в инициализированном состоянии и, следовательно, можно использовать.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 `IActiveScript::Clone` Метод является оптимизацией `IPersist*::Save`, `CoCreateInstance`, и `IPersist*::Load`, поэтому состояние нового обработчика скриптов должны быть одинаковыми, в том случае, если состояние исходный обработчик сценариев были сохранены и загружены в новый обработчик сценариев. Именованные элементы повторяются в клонированный обработчика скриптов, но указатели определенного объекта для каждого элемента вы забыли и полученные с помощью [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) метод. Это позволяет идентичные объектную модель с точками входа каждого потока (модели подразделения) для использования.  
  
 Этот метод используется для многопоточного сервера узлов, которые могут выполняться несколько экземпляров и тот же скрипт. Обработчик скриптов может возвращать `E_NOTIMPL`, в этом случае узел можно добиться того же результата с помощью дублирования сохраняемого состояния и создания экземпляра обработчика скриптов с `IPersist*` интерфейс.  
  
 Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)