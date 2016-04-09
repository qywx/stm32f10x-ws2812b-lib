STM32F10x WS2812B library
-------------------------

Synopsis:

    #include "ws2812b.h"

    #define NUM_LEDS    300

    RGB_t leds[NUM_LEDS];

    int main() {
        ws2812b_Init();

        while (1) {
            while (!ws2812b_IsReady()); // wait

            //
            // Fill leds buffer
            //

            ws2812b_SendRGB(leds, NUM_LEDS);
        }
    }

HSV color space:

    #include "ws2812b.h"

    #define NUM_LEDS    300

    HSV_t leds[NUM_LEDS];

    int main() {
        ws2812b_Init();

        while (1) {
            while (!ws2812b_IsReady()); // wait

            //
            // Fill leds buffer
            //

            ws2812b_SendHSV(leds, NUM_LEDS);
        }
    }


Configuration
---------------------------
By default WS2812B connected to PB6, TIM4 CH1.



Select a Power Source for LEDs
--------------------------
The WS2812 requires about 5V to work. It should operate at anywhere between about 4V to 7V, but 5V is readily-available on most boards.

Also consider how much current your LED strip is going to pull. With every single LED on at full brightness, each WS2812 can pull about 60mA (20mA per channel). Even with just ten breakout boards strung together, you’re looking at upwards of a possible 600mA. Yikes! If you’re stringing together a lot of these things, make sure your power supply can provide the necessary current.
