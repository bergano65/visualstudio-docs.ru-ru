---
title: Выполнение модульного теста как 64-разрядного процесса | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6b8dd75f7d293ee4e7dc412b2ff8f1983d936e3a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446261"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Выполнение модульного теста как 64-разрядного процесса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

На 64-разрядном компьютере можно выполнять модульные тесты и получать данные о покрытии кода в рамках 64-разрядного процесса.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Выполнение модульного теста как 64-разрядного процесса  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Выполнение модульного теста как 64-разрядного процесса  
  
1. Если код или тесты были скомпилированы как 32-разрядные (x86), но вы хотите выполнять их в 64-разрядном процессе, перекомпилируйте их в конфигурации **Любой ЦП** или при необходимости **64 разряда**.  
  
    > [!TIP]
    > Для максимальной гибкости тестовые проекты следует компилировать в конфигурации **Любой ЦП**. Тогда выполнение возможно как на 32-разрядных, так и на 64-разрядных агентах. Компиляция тестовых проектов в конфигурации **64 разряда** не дает никаких преимуществ.  
  
2. В меню Visual Studio выберите **Тест**, а затем **Параметры** и **Архитектура процессора**. Выберите **x64**, чтобы выполнять тесты в 64-разрядном процессе.  
  
     \- или -  
  
     Укажите `<TargetPlatform>x64</TargetPlatform>` в RUNSETTINGS-файле. Преимущество этого метода состоит в том, что можно задавать группы настроек в разных файлах и быстро переключаться между различными настройками. Кроме того, вы можете копировать настройки между решениями. Дополнительные сведения см. в разделе [Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)   
 [Модульное тестирование кода](../test/unit-test-your-code.md)   
 [Указание параметров тестирования для тестов Visual Studio](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
