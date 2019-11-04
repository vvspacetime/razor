cmake_minimum_required(VERSION 3.14)
project(razor)

set(CMAKE_C_STANDARD, 14)

include_directories(/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1/)
include_directories(bbr)
include_directories(cc)
include_directories(common)
include_directories(estimator)
include_directories(pacing)
include_directories(remb)
include_directories(sim_transport)
include_directories(test)
include_directories(sim_test)
include_directories(sim_test/unix_log)
aux_source_directory(bbr bbr_src)
aux_source_directory(cc cc_src)
aux_source_directory(common common_src)
aux_source_directory(common/platform/posix common_posix_src)
aux_source_directory(estimator estimator_src)
aux_source_directory(pacing pacing_src)
aux_source_directory(remb remb_src)
aux_source_directory(sim_test/unix_log sim_test_unix_log_src)
aux_source_directory(sim_transport sim_transport_src)
add_executable(razor_receiver
        ${bbr_src}
        ${cc_src}
        ${common_src}
        ${common_posix_src}
        ${estimator_src}
        ${pacing_src}
        ${remb_src}
        ${sim_test_unix_log_src}
#        sim_test/unix_log/audio_log.cpp
        ${sim_transport_src}
        sim_test/sim_receiver/sim_receiver_test.cpp
#        sim_test/sim_relay/relay.c
#        sim_test/sim_sender/sim_sender_test.cpp
        )

add_executable(razor_sender
        ${bbr_src}
        ${cc_src}
        ${common_src}
        ${common_posix_src}
        ${estimator_src}
        ${pacing_src}
        ${remb_src}
        ${sim_test_unix_log_src}
        #        sim_test/unix_log/audio_log.cpp
        ${sim_transport_src}
        sim_test/sim_sender/sim_sender_test.cpp
        #        sim_test/sim_relay/relay.c
        #        sim_test/sim_sender/sim_sender_test.cpp
        )