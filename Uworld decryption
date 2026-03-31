inline uint64_t DecryptUWorld(uint64_t world)
{
    return ~std::rotl(world, 32) ^ 0x97F199673D1F48C6uLL;
}

//example usage
uintptr_t EncryptedUWorld = Driver->read<uintptr_t>(Driver->BaseAddress + offsets::UWorld);
uintptr_t DecryptedUWorld = DecryptUWorld(EncryptedUWorld);

uintptr_t UWorld = DecryptedUWorld;
