---
title: "Запуск | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Запуск
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Start** — это параметр программы VSPerfCmd.exe, который инициализирует профилировщик для использования указанного метода профилирования.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Параметры  
 `Method`  
 Должен быть равным одному из следующих ключевых слов:  
  
-   **TRACE** — задает метод инструментирования;  
  
-   **SAMPLE** — задает метод выборки;  
  
-   **COVERAGE** — задает покрытие кода.  
  
-   **CONCURRENCY** — определяет метод конфликтов ресурсов.  
  
## Обязательные параметры  
 Если в командной строке задан параметр **Start**, необходимо указать параметр **Output**.  
  
 **Output:** `filename`  
 Задает имя выходного файла.  
  
## Монопольные параметры  
 Следующие параметры могут использоваться только с параметром **Start** в командной строке.  
  
 **CrossSession**&#124;**CS**  
 Включает профилирование в нескольких процессах.  Поддерживаются оба имени параметра — **CrossSession** и **CS**.  
  
 **User:**\[`domain\`\]`username`  
 Позволяет клиентам получать доступ к монитору с помощью указанной учетной записи.  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** задает счетчик производительности Windows, который включается в файл данных профилирования в виде метки.  **AutoMark** задает интервал в миллисекундах между сборами файла данных.  
  
## Недопустимые параметры  
 Следующие параметры не могут использоваться с параметром **Start** в командной строке.  
  
 **Status**  
 Параметр **Status** применяется к процессам, для которых выполняется профилирование.  Этот параметр перечисляет процессы и потоки и их текущее состояние профилирования \(On\/Off\).  Например, если процесс остановлен, параметр **Status** не отразит это в отчете.  **Status** показывает, выполняется ли профилирование для процесса или нет.  
  
 **Shutdown**\[**:**`Timeout`\]  
 Отключает профилировщик.  
  
## Пример  
 В следующем примере кода показано, как с помощью параметра VSPerfCmd.exe **Start** инициализировать профилировщик.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)