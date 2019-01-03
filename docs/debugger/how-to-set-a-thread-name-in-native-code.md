---
title: Как выполнить Установка имени потока в машинном коде | Документация Майкрософт
ms.custom: ''
ms.date: 12/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9226e009936d0a644a5a6fcfcaba57bc3af25d7d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803102"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Как выполнить Установка имени потока в машинном коде
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков позволяет отслеживать их в окне **Потоки**.

## <a name="set-a-thread-name"></a>Установка имени потока

`SetThreadName` Функция может быть полезна для настройки и просмотра обсуждений, если присоединен отладчик для запуска кода. Начиная с Visual Studio 2017 версии 15.6, можно использовать [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) функцию, чтобы задать и просмотреть имена потоков.

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

## <a name="set-a-thread-name-using-setthreadname"></a>Установка имени потока с помощью SetThreadName

Для задания имени потока в программе, можно также использовать `SetThreadName` функции, как показано в следующем примере кода. Обратите внимание, что имя потока копируется в поток, чтобы можно было освободить память для параметра `threadName` .  Этот метод использует подход на основе на исключение, которое работает, только если во время в методе, основанной на исключении подключен отладчик. Имя потока, который задан с помощью этого метода будет недоступен в дампы или средства анализа производительности.

В следующем примере кода показано, как использовать `SetThreadName`:

```C++
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
```  

## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Практическое руководство. Установка имени потока в управляемом коде](../debugger/how-to-set-a-thread-name-in-managed-code.md)