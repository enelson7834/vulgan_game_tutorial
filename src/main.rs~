use vulkan_game_tutorial::utility::constants::*;
use ash::{vk, Entry, version::EntryV1_0, version::InstanceV1_0};

use sdl2::event::Event;
use sdl2::keyboard::Keycode;

use std::ffi::CString;	
use std::ptr;

fn main() {
    // Create vulkan instance 
    let app_name = CString::new(WINDOW_TITLE).unwrap();
    let engine_name = CString::new("Vulkan Engine").unwrap();
    let app_info = vk::ApplicationInfo {
        s_type : vk::StructureType::APPLICATION_INFO,
        p_next : ptr::null(),
        p_application_name : app_name.as_ptr(),
        application_version : APPLICATION_VERSION,
        p_engine_name : engine_name.as_ptr(),
        engine_version : ENGINE_VERSION,
        api_version : API_VERSION,
    };

    unsafe {
        let entry = Entry::new().expect("Failed to create entry.");
    }

    // SDL init & create window
    let sdl_context = sdl2::init().unwrap();
    let video_subsystem = sdl_context.video().unwrap();

    let window = video_subsystem.window(WINDOW_TITLE, WINDOW_HEIGHT, WINDOW_WIDTH)
        .vulkan()
        .position_centered()
        .build();

    // main loop
    let mut event_pump = sdl_context.event_pump().unwrap();

    'running: loop {
        for event in event_pump.poll_iter() {
            match event {
                Event::Quit {..} |
                Event::KeyDown { keycode: Some(Keycode::Escape), .. } => {
                    break 'running
                },
                _ => {}
            }
        }

        ::std::thread::sleep(::std::time::Duration::new(0, 1_000_000_000u32 / 60));
    }

    // cleanup() handeled by drop()
}
