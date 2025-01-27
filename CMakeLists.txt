cmake_minimum_required(VERSION 3.1)

project(mc_panda_mujoco VERSION 1.0.0)

find_package(mc_mujoco REQUIRED)
find_package(mc_panda REQUIRED)

set(SHARE_DESTINATION "${CMAKE_INSTALL_PREFIX}/share/mc_panda/mujoco")
set(Panda_PDGAINS_PATH "pdgains/PDgains_sim.dat")

# if(SRC_MODE)

#   set(Panda_PDGAINS_PATH "${CMAKE_CURRENT_SOURCE_DIR}/${Panda_PDGAINS_PATH}")
# else()

set(Panda_PDGAINS_PATH "${SHARE_DESTINATION}/${Panda_PDGAINS_PATH}")
# endif()

install(DIRECTORY meshes DESTINATION "${SHARE_DESTINATION}")

install(FILES panda_default.xml DESTINATION "${SHARE_DESTINATION}")
install(FILES panda_foot.xml DESTINATION "${SHARE_DESTINATION}")
install(FILES panda_fist.xml DESTINATION "${SHARE_DESTINATION}")
install(FILES panda_push.xml DESTINATION "${SHARE_DESTINATION}")
install(FILES panda_hand.xml DESTINATION "${SHARE_DESTINATION}")
install(FILES panda_pump.xml DESTINATION "${SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_hand.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_hand.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_hand.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_default.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_default.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_default.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_foot.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_foot.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_foot.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_fist.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_fist.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_fist.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_push.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_push.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_push.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

configure_file(mc_mujoco/panda_pump.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/panda_pump.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/panda_pump.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

# install(DIRECTORY pdgains DESTINATION "${SHARE_DESTINATION}" FILES_MATCHING PATTERN "*.dat")
install(DIRECTORY pdgains DESTINATION "${SHARE_DESTINATION}" FILES_MATCHING PATTERN "*.dat")