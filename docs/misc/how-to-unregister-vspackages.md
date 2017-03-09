---
title: "Практическое руководство. Отмена регистрации пакетов VSPackage | Microsoft Docs"
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
  - "учебные приложения [Visual Studio SDK], удаление"
  - "установка, пакеты VSPackage"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Практическое руководство. Отмена регистрации пакетов VSPackage
По умолчанию при выполнении сборки пакетов VSPackage они регистрируются в экспериментальном кусте реестра. Ваш экспериментальный куст может быть заполнен пакетами VSPackage, которые вы не собираетесь сохранять после экспериментов с ними.  
  
 Чтобы удалить все пакеты, зарегистрированные в экспериментальном кусте, сбросьте этот куст, используя средство CreateExpInstance с параметром \/Reset. Для получения дополнительной информации см. [Экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
## Отмена регистрации отдельных пакетов VSPackage  
  
#### Отмена регистрации неуправляемого VSPackage  
  
1.  Нажмите кнопку **Пуск**, выберите **Выполнить**, введите `regsvr32 /u`*pathToVSPackage.dll* и нажмите кнопку "ОК".  
  
 Так как неуправляемые пакеты VSPackage содержат код автоматической регистрации, вы можете использовать программу regsvr32 для их регистрации или отмены регистрации.  
  
#### Отмена регистрации управляемого VSPackage  
  
1.  Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите тип *путь установки Visual Studio SDK*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll*, а затем нажмите кнопку "ОК".  
  
 Средство RegPkg считывает атрибуты регистрации, которые могут быть внедрены в управляемом VSPackage. Параметр **\/unregister** указывает средству RegPkg удалить данные из реестра.  
  
## См. также  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/ru-ru/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)