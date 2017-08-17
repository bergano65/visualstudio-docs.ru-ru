---
title: "Как: управление закрытой коллекции с помощью параметров реестра | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: 00c42a4dbd6a9a526d661b7fa04793d531acd8bc
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Как: управление закрытой коллекции с помощью параметров реестра
Если администратор или разработчик расширение изолированной оболочки, доступ к элементам управления, шаблонов и инструменты в коллекции Visual Studio, галереи примеров или закрытые коллекции можно управлять. Чтобы сделать галереи доступна или недоступна, создайте pkgdef-файл, описывающий ключи реестра и их значения.  
  
## <a name="managing-private-galleries"></a>Управление закрытые галереи  
 Можно создать pkgdef-файл для управления доступом к коллекциям на нескольких компьютерах. Этот файл должен иметь следующий формат.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Ключ ссылается на библиотеке, чтобы включить или отключить. В коллекции Visual Studio и галереи примеров использования репозитории следующие идентификаторы GUID:  
  
-   Коллекция Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Коллекция примеров: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 `Disabled` Значение является необязательным. По умолчанию включены галереи.  
  
 `Priority` Значение определяет порядок, в котором галереях перечислены в диалоговом окне параметров. Коллекция Visual Studio имеет приоритет 10 и коллекции примеров имеет приоритет 20. Закрытые коллекции начинаются с приоритетом 100. Если несколько коллекции имеют одинаковое значение приоритета, порядок, в котором они появляются определяется по значениям их локализованные `DisplayName` атрибуты.  
  
 `Protocol` Значение является обязательным для галереи Atom или SharePoint.  
  
 Либо `DisplayName`, или оба `DisplayNameResourceID` и `DisplayNamePackageGuid`, должен быть указан. Если указан all, то `DisplayNameResourceID` и `DisplayNamePackageGuid` используется пара.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Отключение коллекции Visual Studio, с помощью pkgdef-файл  
 Вы можете отключить галереи в pkgdef-файл. Следующая запись отключает коллекции Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Следующая запись отключает коллекции примеров:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>См. также  
 [Частные коллекции](../extensibility/private-galleries.md)
