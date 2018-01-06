---
title: "Как: изменить пространство имен доменного языка | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3d0dbf6c74c309972862db460f2536d8c6b16801
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Практическое руководство. Изменение пространства имен доменного языка
Можно изменить пространство имен доменного языка. Необходимо внести изменения в **обозреватель DSL**, в свойствах проекта Dsl пакета и сведения о сборке.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Чтобы изменить пространство имен доменного языка  
  
1.  В **обозреватель DSL**, нажмите кнопку **Dsl** узла.  
  
2.  В **свойства** измените **имен** свойство.  
  
3.  Сохраните решение и преобразования шаблонов.  
  
4.  На **проекта** меню, нажмите кнопку **Dsl свойства**.  
  
     Отобразятся свойства проекта.  
  
5.  Перейдите на вкладку **Приложение** .  
  
6.  Изменение **пространство имен по умолчанию** новое имя пространства имен.  
  
7.  Если требуется изменить имя сборки, измените **свойство имени сборки.**  
  
8.  Если вы изменили имя сборки, откройте DslPackage\Package.tt и обновить эту строку:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Если вы написали настраиваемый код, убедитесь, что изменение ссылки на пространство имен и класс в файлах кода.  
  
10. Сброс в экспериментальном экземпляре Visual Studio.  
  
    1.  Удалить **\Users\\***{имя}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  В ОС Windows **запустить** меню, выберите **все программы**, **Microsoft Visual Studio 2010 SDK**, **средства**, **сброса Экспериментальный экземпляр**.  
  
11. На **построения** меню, выберите **Перестроить решение**.  
  
## <a name="see-also"></a>См. также  
 [Глоссарий инструменты доменного языка](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)