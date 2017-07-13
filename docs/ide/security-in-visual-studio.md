---
title: "Безопасность в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 7314921a9416184c4bd63312bd5a82cef4102ddd
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# Безопасность в Visual Studio
<a id="security-in-visual-studio" class="xliff"></a>
Вопросы безопасности должны рассматриваться на всех этапах разработки приложения — от проектирования до развертывания. Начните работу с запуска Visual Studio в наиболее безопасном режиме. См. раздел [Разрешения пользователей](../ide/user-permissions-and-visual-studio.md).  
  
 Для успешной разработки безопасного приложения следует ознакомиться с основными понятиями безопасности и средствами защиты платформ, для которых разрабатывается приложение. Кроме того, необходимо понимать приемы безопасного кодирования.  
  
## Общее представление о безопасности
<a id="understanding-security" class="xliff"></a>  
 [Безопасность](/dotnet/standard/security/index)  
 Описание управления доступом к коду, ролевой политики безопасности, а также политики и средств безопасности в .NET Framework.  
  
 [Десять советов по защите кода, которые должен знать каждый разработчик](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Вопросы, внимание к которым позволит избежать возникновения угрозы безопасности для данных или системы.  
  
## Безопасное кодирование
<a id="coding-for-security" class="xliff"></a>  
 Большинство ошибок кодирования, которые приводят к уязвимости системы безопасности, происходит из-за неправильных допущений разработчиков при работе с вводимыми пользователем данными или из-за неполного понимания принципов работы платформы, для которой разрабатывается приложение.  
  
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)  
 Правила классификации компонентов для решения вопросов безопасности.  
  
 [Рекомендации по безопасности](/cpp/top/security-best-practices-for-cpp)  
 Описание переполнения буфера и общая картина функциональности проверки безопасности в Microsoft Visual C++, которая включается с помощью флага времени компиляции /GS.

## Безопасная сборка
<a id="building-for-security" class="xliff"></a>  
 При сборке безопасность играет немаловажную роль.  Выполнив дополнительные процедуры, можно повысить безопасность развернутого приложения и защитить его от несанкционированного реконструирования, спуфинга и других атак.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Здесь объясняется, как настроить и начать использовать бесплатное решение Dotfuscator Community Edition с PreEmptive Protection для защиты сборок .NET от реконструирования и несанкционированного использования (например, несанкционированная отладка).
  
 [Управление сборками и подписывание манифестов](managing-assembly-and-manifest-signing.md)  
 Здесь рассматривается подписывание с использованием строгих имен, которое можно применять для уникальной идентификации программных компонентов, предотвращая таким образом спуфинг.
