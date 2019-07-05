---
title: Практическое руководство. Управление закрытой галереей с помощью параметров реестра | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b4f33f7ecf974fe527f814b9febdc861101f1ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318496"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Практическое руководство. Управление частной галереей с помощью параметров реестра
Если вы являетесь администратором или разработчиком расширение изолированной оболочки, вы можете управлять доступом к элементам управления, шаблонов и средств в коллекции Visual Studio, коллекции примеров или закрытые коллекции. Чтобы сделать коллекции доступен или недоступен, создать *.pkgdef* файл, описывающий ключи реестра и их значения.

## <a name="manage-private-galleries"></a>Управление закрытые коллекции
 Можно создать *.pkgdef* для управления доступом к коллекциям на нескольких компьютерах. Этот файл должен иметь следующий формат.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories` Ключ ссылается на коллекции, чтобы включить или отключить. В коллекции Visual Studio и галереи примеров используют следующий репозиторий идентификаторы GUID:

- Коллекции Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Коллекция примеров: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled` Значение является необязательным. По умолчанию включен коллекции.

  `Priority` Значение определяет порядок, в котором перечислены галереях в **параметры** диалоговое окно. Коллекции Visual Studio имеет приоритет 10 и в коллекции примеров имеет приоритет 20. Закрытые коллекции начинаются с приоритетом 100. Если несколько коллекций имеют одинаковое значение приоритета, порядок, в котором они появляются определяется по значениям их локализованные `DisplayName` атрибуты.

  `Protocol` Значение является обязательным для коллекции на основе SharePoint или веб-каналов Atom.

  Либо `DisplayName`, или оба `DisplayNameResourceID` и `DisplayNamePackageGuid`, должен быть указан. Если все заданы, то `DisplayNameResourceID` и `DisplayNamePackageGuid` используется пара.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Отключение коллекции Visual Studio, с помощью файла .pkgdef
 Вы можете отключить коллекции в *.pkgdef* файл. Следующая запись будет отключено в коллекции Visual Studio.

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Следующая запись будет отключено в коллекции примеров.

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>См. также
- [Закрытые коллекции](../extensibility/private-galleries.md)