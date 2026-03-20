Changes

++Fortnite+Release-40.00-CL-51746096-Windows

SDK: ++Fortnite+Release-40.00-CL-51746096-Windows

Global Offsets
GWorld: 0x193717F0
GEngine: 0x19373048
GNames: 0x19230DC0

inline uintptr_t GetGWorld() {
    auto GWorld = DotMem::Read<uintptr_t>(DotMem::BaseAddress + 0x193717F0);
    if (!GWorld) return NULL;
    return _rotl64(GWorld, 32) ^ 0x97F199673D1F48C6uLL;
}

struct FInstancedStruct
{
    uintptr_t ScriptStruct;
    uintptr_t StructMemory;
};
 
EFortRarity GetRarity(uintptr_t itemDefinition) {
    auto DataList = DotMem::Read<TArray<FInstancedStruct>>(itemDefinition + 0x68);
    for (auto i = 0; i < DataList.Num(); i++) {
        auto Data = DataList[i];
        if (Data.ScriptStruct == DotMem::BaseAddress + 0x16946C78) { // FortItemComponentData_Rarity struct
            return DotMem::Read<EFortRarity>(Data.StructMemory);
        }
    }

    return EFortRarity::EFortRarity_Common;
}

Functions

StaticFindObject: 0x573AD2
UObject::ProcessEvent: 0xA108A (Index: 0x37)
Other Offsets
UObject.ObjectFlags: 0x8
UObject.InternalIndex: 0xc
UObject.OuterPrivate: 0x10
UObject.NamePrivate: 0x18
UObject.ObjectListInternalIndex: 0x1c
UObject.ClassPrivate: 0x20

UStruct.PropertiesSize: 0x70
UStruct.MinAlignment: 0x58
UStruct.SuperStruct: 0x60
UStruct.Children: 0xa8
UStruct.ChildProperties: 0x98

FField.Owner: 0x20
FField.Next: 0x8
FField.ClassPrivate: 0x10

FFieldClass.CastFlags: 0x18
