---
title: "Практическое руководство: управление закрытой галереей с помощью параметров реестра | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Частные коллекции VSIX, управление"
  - "Управление частные коллекции VSIX"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: управление закрытой галереей с помощью параметров реестра
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если администратор или разработчик расширение изолированной оболочки, можно управлять доступом к элементы управления, шаблоны и средства в коллекции Visual Studio, Коллекция примеров или частные коллекции. Чтобы сделать коллекция доступна или недоступна, создайте pkgdef\-файл, описывающий ключи реестра и их значения.  
  
## Управление закрытого галереях  
 Можно создать pkgdef\-файл для управления доступом к коллекции на нескольких компьютерах. Этот файл должен иметь следующий формат.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Ключ относится к коллекции, чтобы включить или отключить. Коллекции Visual Studio и галереи примеров используйте репозитории следующий GUID:  
  
-   Коллекция Visual Studio: 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   Коллекция примеров: AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 `Disabled` Значение является необязательным. Коллекция включена по умолчанию.  
  
 `Priority` Значение определяет порядок, в котором перечислены коллекции в диалоговом окне Параметры. Коллекция Visual Studio имеет приоритет 10 и коллекции примеров имеет приоритет 20. Частные коллекции начинаются с приоритетом 100. Если несколько коллекций имеют одинаковое значение приоритета, порядок, в котором они появляются определяется по значениям их локализованные `DisplayName` атрибуты.  
  
 `Protocol` Значение является обязательным для коллекции, основанные на Atom или SharePoint.  
  
 Либо `DisplayName`, или оба `DisplayNameResourceID` и `DisplayNamePackageGuid`, должен быть указан. Если указан all, то `DisplayNameResourceID` и `DisplayNamePackageGuid` используется пара.  
  
## Отключение коллекции Visual Studio с помощью pkgdef\-файл  
 Можно отключить коллекции в pkgdef\-файл. Следующая запись отключает коллекции Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Следующая запись отключает коллекции примеров:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## См. также  
 [Частные коллекции](../extensibility/private-galleries.md)