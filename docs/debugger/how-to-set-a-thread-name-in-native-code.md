---
title: Как задать имя потока в машинном коде | Документация Майкрософт
ms.date: 12/17/2018
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a89dce28f33bef0ffdb13d6254b2ac6b86ac25db
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589025"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Практическое руководство. Установка имен потока в машинном коде
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков полезно для определения интересующих потоков в окне **потоков** при отладке выполняющегося процесса. Наличие распознаваемых именованных потоков также может оказаться полезным при выполнении отладки после аварийного завершения с помощью проверки дампа памяти и при анализе захвата производительности с помощью различных средств.

## <a name="ways-to-set-a-thread-name"></a>Способы задания имени потока

Существует два способа задать имя потока. Первый — через функцию [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . Второй — создание определенного исключения, когда отладчик Visual Studio прикрепляется к процессу. Каждый подход имеет свои преимущества и предостережения. Использование `SetThreadDescription` поддерживается начиная с Windows 10, версии 1607 или Windows Server 2016.

Стоит отметить, что при необходимости _оба_ подхода можно использовать вместе, так как механизмы, по которым они работают, независимы друг от друга.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Задайте имя потока с помощью `SetThreadDescription`

Преимущества:
* Имена потоков отображаются при отладке в Visual Studio независимо от того, был ли отладчик присоединен к процессу во время вызова SetThreadDescription.
* Имена потоков отображаются при выполнении отладки после неустранимой нагрузки путем загрузки аварийного дампа в Visual Studio.
* Имена потоков также отображаются при использовании других средств, таких как отладчик [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) и анализатор производительности [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) .

Предупреждения:
* Имена потоков отображаются только в Visual Studio 2017 версии 15,6 и более поздних версиях.
* При отладке файла аварийного дампа после аварии имена потоков отображаются только в том случае, если сбой был создан в Windows 10 версии 1607, Windows Server 2016 или более поздних версиях Windows.

*Пример:*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Задать имя потока, вызывая исключение

Другим способом задать имя потока в программе является передача нужного имени потока отладчику Visual Studio, вызывая специально настроенное исключение.

Преимущества:
* Работает во всех версиях Visual Studio.

Предупреждения:
* Работает только в том случае, если отладчик присоединен к моменту использования метода, основанного на исключениях.
* Имена потоков, заданные с помощью этого метода, не будут доступны в дампах или средствах анализа производительности.

*Пример:*

Приведенная ниже функция `SetThreadName` демонстрирует этот подход на основе исключений. Обратите внимание, что имя потока будет автоматически скопировано в поток, чтобы память для параметра `threadName` можно было освободить после завершения вызова `SetThreadName`.

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

## <a name="see-also"></a>См. также раздел
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)
- [Практическое руководство. Установка имени потока в управляемом коде](../debugger/how-to-set-a-thread-name-in-managed-code.md)
