---
title: "Библиотека Visual Studio, обзор | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Библиотека Visual Studio, обзор"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Библиотека Visual Studio, обзор
Библиотека Visual Studio набор шаблон\-основанных классов C\+\+ для упрощение создание VSPackages в собственном C\+\+.  Библиотека Visual Studio включает полный исходный код, например набор файлов заголовков C\+\+.  Файлы заголовков, устанавливаются в пределах *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ источник \\ CPP \\ VSL \\ включают \\.  
  
> [!NOTE]
>  Библиотека Visual Studio основана на библиотеку шаблонных классов ATL \(библиотека ATL\) для их поддержки COM\-объект.  Дополнительные сведения см. в разделе [Введение в ATL](/visual-cpp/atl/introduction-to-atl).  
  
 Библиотека Visual Studio поддерживают модульное тестирование и для собственного кода, а для кода.  Некоторые модульные тесты, следующим образом:  
  
-   Модульные тесты библиотеки устанавливаются в Visual Studio *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ источник \\ CPP \\ \\. \\ VSL UnitTest  
  
-   Базовые классы для модульных тестов для кода в *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ источник \\ CPP \\ VSL \\ include \\ VSLUnitTest.h.  
  
 Часто используемых насмешливые реализации интерфейсов модели COM и Visual Studio в файлах заголовков, VSLMockSystemInterfaces.h и VSLMockVisualStudioInterfaces.h, которые устанавливаются в пределах *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ источник \\ CPP \\ VSL \\ включают \\.  
  
## См. также  
 [Разработка пакетов VSPackage с помощью библиотеки Visual Studio](../misc/developing-vspackages-by-using-the-visual-studio-library.md)