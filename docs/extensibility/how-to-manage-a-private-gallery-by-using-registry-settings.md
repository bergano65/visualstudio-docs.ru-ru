---
title: Руководство. Управление частной галереей с помощью параметров реестра | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710932"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Руководство. Управление частной галереей с помощью параметров реестра
Если вы являетесь администратором или разработчиком изолированного расширения оболочки, вы можете управлять доступом к элементам управления, шаблонам и средствам в коллекции Visual Studio, коллекции примеров или частных галереях. Чтобы сделать коллекцию доступной или недоступной, создайте файл *pkgdef* , описывающий измененные разделы реестра и их значения.

## <a name="manage-private-galleries"></a>Управление частными галереями
 Можно создать файл *pkgdef* для управления доступом к галереям на нескольких компьютерах. Этот файл должен иметь следующий формат.

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

 `Repositories`Ключ ссылается на коллекцию, которая должна быть включена или отключена. В коллекции Visual Studio и коллекции примеров используются следующие идентификаторы GUID репозитория:

- Коллекция Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Коллекция примеров: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`Значение является необязательным. По умолчанию коллекция включена.

  `Priority`Значение определяет порядок, в котором галереи перечислены в диалоговом окне **Параметры** . У коллекции Visual Studio приоритет 10, а в галерее Samples — приоритет 20. Частные коллекции начинаются с приоритета 100. Если несколько коллекций имеют одинаковое значение приоритета, порядок их отображения определяется значениями их локализованных `DisplayName` атрибутов.

  `Protocol`Значение является обязательным для коллекций на основе Atom или SharePoint.

  `DisplayName`Необходимо указать либо, либо, `DisplayNameResourceID` и `DisplayNamePackageGuid` , и. Если указаны все, то `DisplayNameResourceID` `DisplayNamePackageGuid` используется пара и.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Отключение коллекции Visual Studio с помощью файла pkgdef
 Коллекцию можно отключить в файле *pkgdef* . Следующая запись отключает коллекцию Visual Studio:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Следующая запись отключает коллекцию Samples:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>См. также раздел
- [Частные галереи](../extensibility/private-galleries.md)
