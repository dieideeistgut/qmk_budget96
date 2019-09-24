# Custom Keymap & Stuff for budget96

Added to budget96.c:

```
void matrix_init_kb(void) {
#ifdef RGBLIGHT_ENABLE
    if (rgblight_config.enable) {
        i2c_init();
        i2c_transmit(0xb0, (uint8_t*)led, 3 * RGBLED_NUM, 100);
    }
#endif
    // call user level keymaps, if any
    matrix_init_user();
}

void matrix_scan_kb(void) {
#ifdef RGBLIGHT_ENABLE
    rgblight_task();
#endif
    matrix_scan_user();
    /* Nothing else for now. */
}
```

Also see https://github.com/kaylanm/qmk_firmware/blob/e8b469e026be08e5fa0d26c8e0c920a2cc0d955b/keyboards/singa/singa.c
