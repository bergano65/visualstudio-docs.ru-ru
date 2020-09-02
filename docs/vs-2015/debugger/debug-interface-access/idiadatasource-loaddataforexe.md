---
title: 'Идиадатасаурце:: Лоаддатафорексе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 623cdd74b086a46bc52c0f0534953ae6e11168ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547394"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает и готовит данные отладки, связанные с файлом EXE/. dll.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 исполняемый файл  
 окне Путь к exe-или DLL-файлу.  
  
 searchPath  
 окне Альтернативный путь для поиска данных отладки.  
  
 pCallback  
 окне `IUnknown` Интерфейс для объекта, поддерживающего интерфейс обратного вызова отладки, например [идиалоадкаллбакк](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)и/или интерфейсы [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны некоторые возможные коды ошибок для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Не удалось открыть файл, или файл имеет недопустимый формат.|  
|E_PDB_FORMAT|Попытка доступа к файлу с устаревшим форматом.|  
|E_PDB_INVALID_SIG|Сигнатура не совпадает.|  
|E_PDB_INVALID_AGE|Возраст не соответствует.|  
|E_INVALIDARG|Недопустимый параметр.|  
|E_UNEXPECTED|Источник данных уже подготовлен.|  
  
## <a name="remarks"></a>Remarks  
 В заголовке Debug файла exe/. DLL называется связанное расположение данных отладки.  
  
 Этот метод считывает заголовок Debug, а затем ищет и готовит данные отладки. Ход выполнения поиска может при необходимости передаваться и контролироваться с помощью обратных вызовов. Например, [идиалоадкаллбакк:: нотифидебугдир](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) вызывается, когда `IDiaDataSource::loadDataForExe` метод находит и обрабатывает каталог отладки.  
  
 Интерфейсы [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) и [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) позволяют клиентскому приложению предоставлять альтернативные методы для чтения данных из исполняемого файла, когда доступ к файлу осуществляется напрямую через стандартный файловый ввод-вывод.  
  
 Чтобы загрузить PDB-файл без проверки, используйте метод [идиадатасаурце:: лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Чтобы проверить PDB-файл на соответствие конкретным критериям, используйте метод [идиадатасаурце:: лоадандвалидатедатафромпдб](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Чтобы загрузить PDB-файл непосредственно из памяти, используйте метод [идиадатасаурце:: лоаддатафромистреам](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Пример  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md)   
 [идиалоадкаллбакк](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Идиалоадкаллбакк:: Нотифидебугдир](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Идиадатасаурце:: Лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Идиадатасаурце:: Лоадандвалидатедатафромпдб](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
