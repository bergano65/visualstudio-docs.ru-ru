---
title: "Определение требований к системе | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "установка, пакеты VSPackage"
  - "условия запуска"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# Определение требований к системе
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage не может работать, если не установлена среда Visual Studio. При использовании установщика Windows для управления установкой VSPackage, можно настроить установщик, чтобы определить, установлена ли среда Visual Studio. Также можно настроить его, чтобы проверить в системе другие требования, например, определенной версии Windows или определенный объем оперативной памяти.  
  
## Обнаружение выпуски Visual Studio  
 Чтобы определить, установлен ли выпуск Visual Studio, проверьте значение ключа реестра установки \(REG\_DWORD\) 1 в соответствующей папке, перечисленные в следующей таблице. Обратите внимание, что иерархии из выпусков Visual Studio:  
  
1.  Предприятие  
  
2.  Professional  
  
3.  Сообщество  
  
 При установке «высокого» выпуска добавляются разделы реестра для этого выпуска, также как выпуски «ниже». То есть если установлен выпуск Enterprise edition, ключ установки равен 1 для предприятия, а также в выпусках Professional и сообщества. Поэтому необходимо проверять только выпуск «высокий», необходимые.  
  
> [!NOTE]
>  В 64\-разрядной версии редактора реестра 32\-разрядные разделы отображаются в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\. Visual Studio ключи находятся под HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\.  
  
|Продукт|Ключ|  
|-------------|----------|  
|Visual Studio Enterprise|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Оболочка Visual Studio 2015 \(интегрированной и изолированный\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Обнаружение при запуске Visual Studio  
 Не удается зарегистрировать VSPackage правильно, если Visual Studio выполняется при установке VSPackage. Установщик должен обнаружить при запуске Visual Studio и затем отклонить для установки программы. Установщик Windows не позволяет использовать для обнаружения таких записей в таблице. Вместо этого необходимо создать настраиваемое действие, следующим образом: использование `EnumProcesses` функция обнаружения процесса devenv.exe и затем установите свойство установщика, используемого в условии запуска или условно отображать диалоговое окно, пользователю предлагается закрыть Visual Studio.  
  
## См. также  
 [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)